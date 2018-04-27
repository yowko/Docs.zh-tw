### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>資料定義語言 (DDL) API 的行為變更

|   |   |
|---|---|
|詳細資料|指定 AttachDBFilename 時，DDL API 的行為已變更如下：<ul><li>連接字串不需要指定 Initial Catalog 值。 以往 AttachDBFilename 和 Initial Catalog 都是必要項。</li><li>如果同時指定 AttachDBFilename 和 Initial Catalog，且指定的 MDF 檔案存在，則 ObjectContext.DatabaseExists 方法會傳回 true。 以往它會傳回 false。</li><li>如果同時指定 AttachDBFilename 和 Initial Catalog，且指定的 MDF 檔案存在，則呼叫 ObjectContext.DeleteDatabase 方法會刪除檔案。</li><li>如果是在連接字串指定 AttachDBFilename 值，而其中 MDF 不存在且 Initial Catalog 也不存在時呼叫 ObjectContext.DeleteDatabase，則方法會擲回 InvalidOperationException 例外狀況。 以往它會擲回 SqlException 例外狀況。</li></ul>|
|建議|這些變更可讓您更容易建置使用 DDL 應用程式開發介面的工具和應用程式。 在下列情節中，這些變更可能會影響應用程式相容性：<ul><li>如果 ObjectContext.DatabaseExists 傳回 true，使用者撰寫的程式碼會直接執行 DROP DATABASE 命令，而不是呼叫 ObjectContext.DeleteDatabase。 如果未附加資料庫，但 MDF 檔案存在，則會使現有的程式碼中斷。</li><li>當 Initial Catalog 和 MDF 檔案不存在時，使用者撰寫的程式碼預期 ObjectContext.DeleteDatabase 方法擲回 SqlException 例外狀況，而不是 InvalidOperationException 例外狀況。</li></ul>|
|範圍|次要|
|版本|4.5|
|類型|執行階段|

