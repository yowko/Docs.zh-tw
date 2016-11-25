# <a name="using-the-cli-preview3-folder-and-sub-folders"></a>使用 cli-preview3 資料夾與子資料夾

此資料夾是符合工具資料夾的最上層節點，但是包含 .NET Core 工具 Preview 3 版本的差異。

此個別的平行資料夾結構的目標是提供一個位置，讓 Preview 3 版本相關內容可以在發行網站中提供版本切換時，相對容易地合併到主要結構中。

此節點下的內容應該為較小的文件組，可代表來自長期支援 (LTS) 版本與最新的目前版本的差異。 

## <a name="structure"></a>結構

新增此版本的新內容有兩種情況：

* 現有文件的變更
    - 將現有的內容複製到此結構下的平行資料夾。 進行變更，並將修改過的檔案新增到 Preview 3 版本的目錄。
* 新文件
    - 將新的文件放在適當的位置，並將它新增到 Preview 3 版本之節點下的目錄。 

所有目前的版本檔案應該在主題頂端附近新增下列項目：

[!include[current release track](../includes/warning.md)]

我們已使用下列語法建立要包含的程式碼片段︰

```markdown
[!include[current release track](../../includes/warning.md)]
```

### <a name="link-instructions"></a>連結指示

在這兩種情況下，針對瀏覽目的提供目前版本的連結到 LTS 頁面 (或是上層 index.md)。
請考慮提供 LTS 頁面連結 (或是上層 index.md) 到新的目前版本內容頁面。

## <a name="future-considerations"></a>未來的考量

我們的最終目標是要將不同的版本呈現為[文件存放庫](https://github.com/dotnet/docs)中的分支。 在支援該發行案例之前，我們將針對各個目前版本使用不同的最上層資料夾。 

當時機成熟時，我們可以將各個目前版本合併到主要 [docs](../docs) 資料夾、合併目錄節點，並發佈為個別文件組。 我們可能需要將修改同時合併到 LTS 版本的檔案以及目前版本的檔案，但是我們應該能相對輕鬆地找出那些變更。


<!--HONumber=Nov16_HO3-->


