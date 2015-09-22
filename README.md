# asp.net-versioning-file
<pre>
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
</pre>
