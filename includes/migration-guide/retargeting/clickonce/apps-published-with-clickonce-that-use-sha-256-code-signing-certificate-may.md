### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>透過 ClickOnce 發行的應用程式，這些應用程式使用可能會在 Windows 2003 上失敗的 SHA-256 程式碼簽署憑證

|   |   |
|---|---|
|詳細資料|這個可執行檔使用 SHA256 簽署。 之前，不論程式碼簽署憑證為 SHA-1 或 SHA-256，都會使用 SHA1 簽署。 這適用於：<ul><li>使用 Visual Studio 2012 (含) 以後版本建置的所有應用程式。</li><li>使用 Visual Studio 2010 (含) 以前版本，在具有 .NET Framework 4.5 的系統上建置應用程式。</li></ul>此外，如果有 .NET Framework 4.5 (含) 以後版本，也會針對 SHA-256 憑證使用 SHA-256 來簽署 ClickOnce 資訊清單，而不論編譯的 .NET Framework 版本為何。|
|建議|對簽署 ClickOnce 可執行檔所做的變更只會影響 Windows Server 2003 系統；這些變更需要安裝 KB 938397。對使用 SHA-256 簽署資訊清單所做的變更還會引進 .NET Framework 4.5 或更新版本的執行階段相依性，即使應用程式是以 .NET Framework 4.0 或更早版本為目標亦然。|
|範圍|Edge|
|版本|4.5|
|類型|正在重定目標|

