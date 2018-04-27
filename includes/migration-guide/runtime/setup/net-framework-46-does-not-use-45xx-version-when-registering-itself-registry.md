### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>.NET Framework 4.6 在登錄中註冊本身時不使用 4.5.x.x 版本

|   |   |
|---|---|
|詳細資料|如預期一般，.NET Framework 4.6 在登錄中的版本機碼設定 (位於 <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) 開頭為 '4.6'，而不是 '4.5'。 相依於這些登錄機碼以得知電腦上所安裝之 .NET Framework 版本的應用程式應該加以更新，才能了解 4.6 是新的可能版本，以及其與先前的 4.5.x 版相容。|
|建議|藉由尋找 4.5 登錄機碼來更新 .NET Framework 4.5 安裝的應用程式探查，使其也接受 4.6。|
|範圍|Edge|
|版本|4.6|
|類型|執行階段|

