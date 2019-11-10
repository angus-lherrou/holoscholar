# ModelBank
v. 1.0.2

## Caveats
Hi, this code is almost completely undocumented outside of this README. Sorry! Please follow these instructions to the letter.

This code has almost no protection against edge cases as of v. 1.0.2, so please be very careful how you implement this. Remember to catch FileNotFoundExceptions!

## Exceptions to catch
* If your model manifest is formatted incorrectly, you MIGHT get a FileLoadException. Don't count on it, but catch it regardless.
* If your page manifest contains model names that don't exist in your book, you'll get a ModelDoesNotExistException. Catch this. 
* Obviously, if you're pointing to files that don't exist, you'll get a FileNotFoundException. Catch!!

## Usage Instructions
1. You'll want two manifest files: a file with model names and directories, and a file with pages and model names. Create these in the following formats:
  * Model Manifest: on each line, a model name, followed by a pipe, followed by a directory (absolute or relative to your code). Use forward slashes or \\escaped backslashes.
    * Example: `Caffeine|c:/Users/Angus/Documents/MyModels/caffeine.obj`
  * Page Manifest: on each line, a series of model names separated by commas.
    * Example: `Caffeine,Hydrochloric Acid,Buckminsterfullerene`
2. Import the nuget package into your code
  1. ```<RestoreSources>$(RestoreSources);absolute-path-to-my-solution/library/bin/Debug;https://api.nuget.org/v3/index.json</RestoreSources>`

3. Create a new `ModelBank` object by constructing it with a name string for your book
4. Add models to your book by calling `<your ModelBank object>.MakeBook(pathToModelManifest)`
5. Add pages to your book by calling `<your ModelBank object>.MakePages(pathToPageManifest)`
6. To get the path to a model file for the `n`th model on the `m`th page, call `<your ModelBank object>.GetPath(m, n)` (both indexed at zero).

## Credits
* Blessed be to Microsoft for their .NET documentation
* Thank you to Sam Stern, Anna Cowett, and Viking Mayor for moral support
* Best of luck to you, Max.