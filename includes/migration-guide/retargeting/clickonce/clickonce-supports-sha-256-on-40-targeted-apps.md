### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce 在 4.0 為目標的應用程式上支援 SHA-256

|   |   |
|---|---|
|詳細資料|先前，具有使用 SHA-256 簽署之憑證的 ClickOnce 應用程式，需要有 .NET 4.5 或更新版本存在，即使應用程式是以 4.0 為目標。 現在，以 4.0 為目標的 ClickOnce 應用程式可以在 4.0 上執行，即使是使用 SHA-256 進行簽署。|
|建議|這項變更移除了該相依性，並允許使用 SHA-256 憑證來簽署以 .NET Framework 4 和更早版本為目標的 ClickOnce 應用程式。|
|範圍|次要|
|版本|4.6|
|類型|正在重定目標|

