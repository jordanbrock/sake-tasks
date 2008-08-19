desc "Install sake tasks, uninstalling any pre-existing tasks first; can pass ONLY_FILES and ONLY_TASKS env vars"
task :install do
  task_files = Dir['**/*.sake']
  only_files = ENV['ONLY_FILES'] && ENV['ONLY_FILES'].split(',')
  only_tasks = ENV['ONLY_TASKS'] && ENV['ONLY_TASKS'].split(',')
  task_files.sort.map do |task_file|
    next if only_files && !only_files.include?(task_file)
    sake_task = task_file.gsub('/', ':').gsub('.sake','')
    next if only_tasks && !only_tasks.include?(sake_task)
    `sake -u #{sake_task}`
    puts `sake -i #{task_file}`
  end
end

task :default => :install