The following 'Groovy system' (requires Groovy plugin) build step script works for Project subclasses, i.e. freestyle projects. This works well enough for me, you might need to adapt for other project types (like Maven).

It prints lists of projects by publisher/build wrapper/builder/trigger, and provides both the builder/... name and the name of the plugin it came in. It assumes Jenkins context is at / (i.e. http://host/ , not http://host/jenkins/ ) for links to jobs. Sorted ascending by number of jobs.

--------

def projects = jenkins.model.Jenkins.instance.getAllItems(hudson.model.Project.class)

def projectsByDescriptor = [:]

for (def p in projects) {
  def items = new ArrayList(p.publishers.values())
  items.addAll(p.builders)
  items.addAll(p.properties.values()) // haven't actually tried this line in an instance that has job properties
  items.addAll(p.triggers.values())
  items.addAll(p.buildWrappers.values())
  items.add(p)
  for (def item in items) {
    def desc = item.descriptor
    if (!projectsByDescriptor.containsKey(desc))
      projectsByDescriptor.put(desc, [])
    if (!projectsByDescriptor[desc].contains(p))
      projectsByDescriptor[desc].add(p)
  }
}

def s = ''<<''
for (def desc in projectsByDescriptor.keySet().sort { projectsByDescriptor.get(it).size() }) {
  s << '<h3>' + desc.displayName + '</h3>\n<small>' + (desc.plugin?.displayName?:'Core') + '</small><ul>'
  for (def proj in projectsByDescriptor.get(desc)) {
    s << "<li><a href=\"/${proj.url}\">${proj.fullDisplayName}</a></li>\n"
  }
  s << '</ul>\n'
}

def ws = Thread.currentThread()?.executable.workspace
  ws.child('report').mkdirs()
  ws.child('report/usage.html').write(s.toString(), 'UTF-8')

--------

This can be made available using the HTML Publisher plugin, folder is 'report', index page 'usage.html'.

WTFPL license if it matters.
Daniel Beck
