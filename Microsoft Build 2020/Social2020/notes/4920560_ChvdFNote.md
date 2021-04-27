# Powering through MSBuild 2020 like
``` csharp
   while(Build.HasActiveSessions)
   {
       Sleep.Skip();
   }
   
   // Greetings from Christoph@Austria
   You
   .MadeIt()
   .Run(() => Sleep.Start());
   ```