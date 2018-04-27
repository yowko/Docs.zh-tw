反斜線 (\\) 是 Mutex 名稱的保留字元。 請勿在 Mutex 名稱中使用反斜線 (\\)，除非在終端機伺服器工作階段中使用 Mutex 的注意事項中有指定。 否則，可能會擲回 <xref:System.IO.DirectoryNotFoundException>，即使是 Mutex 的名稱代表現有的檔案。
