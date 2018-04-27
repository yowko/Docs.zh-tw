### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet.FindClaims 會考慮所有 claimTypes

|   |   |
|---|---|
|詳細資料|在目標為 .NET Framework 4.6.1 的應用程式中，如果 X509 宣告集是初始化自 SAN 欄位中含有多個 DNS 項目的憑證，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> 方法會嘗試使用所有 DNS 項目來比對 claimType 引數。若是以舊版 .NET Framework 為目標的應用程式，則 <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> 方法僅會嘗試使 claimType 引數符合最後一個 DNS 項目。|
|建議|這項變更只會影響以 .NET Framework 4.6.1 為目標的應用程式。 您可以使用 [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) 相容性參數來停用這項變更 (如果以 4.6.1 以前版本為目標則可啟用)。|
|範圍|次要|
|版本|4.6.1|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|

