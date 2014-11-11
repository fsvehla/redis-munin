task :default => [:copy]

task :copy do
     FileList['redis_*_'].each do |f|
         install f, File.join(File::SEPARATOR,"etc","munin","plugins",f) , :mode => 0755,:verbose => true
  end  
end