# Versioning file
```c#
 public static class FileUtility
    {
        public static string GetPathFileWithLastWriteTime(string pRelativePathWithFileName)
        {
            string filePath = HttpContext.Current.Server.MapPath(string.Format("{0}", pRelativePathWithFileName));
            bool fileExist = System.IO.File.Exists(filePath);
            DateTime fInfo = System.IO.File.GetLastWriteTime(filePath);
            if (fileExist)
                return string.Format("{0}?v={1}", pRelativePathWithFileName, fInfo.ToString("yyyymmddHHmmss"));
            return pRelativePathWithFileName;
        }
    }
```
## Getting started
#### 1. Add the class `FileUtility` or method `GetPathFileWithLastWriteTime` in your project
#### 2. Call method `GetPathFileWithLastWriteTime` to files you want to add version
```html
<script src="<%=FileUtility.GetPathFileWithVersion("/assets/scripts/utils.js") %>" type="text/javascript"></script>
<link rel="stylesheet" href="<%=FileUtility.GetPathFileWithVersion("/assets/css/style.css") %>" />
```
Result
```html
<script src="/assets/scripts/utils.js?v=20150922150845" type="text/javascript"></script>
<link rel="stylesheet" href="/assets/css/style.css?v=20150922154552" />
```
