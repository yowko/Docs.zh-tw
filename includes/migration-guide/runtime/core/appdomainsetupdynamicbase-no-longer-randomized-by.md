### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup.DynamicBase 不再由 UseRandomizedStringHashAlgorithm 隨機化

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.6 之前，如果已在應用程式組態檔中啟用 UseRandomizedStringHashAlgorithm，<xref:System.AppDomainSetup.DynamicBase> 的值就會在應用程式定義域或處理序之間隨機化。 從 .NET Framework 4.6 開始，<xref:System.AppDomainSetup.DynamicBase> 將會在執行之應用程式的不同執行個體之間以及不同的應用程式定義域之間，傳回穩定的結果。 動態基底仍會因不同的應用程式而異；這項變更只會移除相同應用程式之不同執行個體的隨機命名項目。|
|建議|請注意，啟用 <code>UseRandomizedStringHashAlgorithm</code> 不會導致 <xref:System.AppDomainSetup.DynamicBase> 隨機化。 如果需要隨機基底，必須在您的應用程式程式碼中產生它，而不是透過此 API 產生。|
|範圍|Edge|
|版本|4.6|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|

