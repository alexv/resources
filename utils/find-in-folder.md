# Find in Folder

Want to programmatically use the 'grep' command in a node environment? Look no further!

Just save the below script somewhere and run...

```
node [path to saved script] [search string] [path to directory to search]
```

### Aformentioned Script

```
const { exec } = require('child_process');

exec(`grep -r ${process.argv[2]} ${process.argv[3]}`, (err, stdout) => {
  if (err) {
    if (err.code === 1){
      console.log(`The string ${process.argv[2]} was not found in directory ${process.argv[3]}.`)
    } else {
      console.log('Error: ' + err)
    }
    return err
  }
  console.log(`The string ${process.argv[2]} was found in directory ${process.argv[3]}.`)
  console.log(stdout)
  return stdout
})
```
