### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>資料定義語言 (DDL) API 的行為變更

|   |   |
|---|---|
|詳細資料|指定 AttachDBFilename 時，DDL API 的行為已變更如下：<ul><li>連接字串不需要指定 Initial Catalog 值。 以往 AttachDBFilename 和 Initial Catalog 都是必要項。</li><li>如果同時指定 AttachDBFilename 和 Initial Catalog，且指定的 MDF 檔案存在，則 <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> 方法會傳回 <code>true</code>。 以往它會傳回 <code>false</code>。</li><li>如果同時指定 AttachDBFilename 和 Initial Catalog，且指定的 MDF 檔案存在，則呼叫 <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> 方法會刪除檔案。</li><li>如果在連接字串指定 AttachDBFilename，而其中 MDF 不存在且初始目錄也不存在時呼叫 <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>，則方法會擲回 <xref:System.InvalidOperationException> 例外狀況。 以往它會擲回 <xref:System.Data.SqlClient.SqlException> 例外狀況。</li></ul>|
|建議|這些變更可讓您更容易建置使用 DDL 應用程式開發介面的工具和應用程式。 在下列情節中，這些變更可能會影響應用程式相容性：<ul><li>如果 <code>DROP DATABASE</code> 傳回 <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>，使用者撰寫的程式碼會直接執行 <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> 命令，而不是呼叫 <code>true</code>。 如果未附加資料庫，但 MDF 檔案存在，則會使現有的程式碼中斷。</li><li>當初始目錄和 MDF 檔案不存在時，使用者撰寫的程式碼預期 <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> 方法會擲回 <xref:System.Data.SqlClient.SqlException>，而不是 <xref:System.InvalidOperationException>。</li></ul>|
|範圍|次要|
|版本|4.5|
|類型|執行階段|

