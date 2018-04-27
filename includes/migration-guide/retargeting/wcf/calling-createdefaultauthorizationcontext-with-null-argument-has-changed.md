### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>使用 Null 引數呼叫 CreateDefaultAuthorizationContext 已變更

|   |   |
|---|---|
|詳細資料|使用 Null authorizationPolicies 引數呼叫 <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> 所傳回的 <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> 實作，已變更其在 .NET Framework 4.6 中的實作。|
|建議|在少數情況下，使用自訂驗證的 WCF 應用程式，在行為上可能會有些許差異。 在此情況下，您可使用下列兩種方式之一還原舊版行為：<ol><li>以 .NET Framework 4.6 之前的舊版為目標，重新編譯您的應用程式。 對於裝載在 IIS 上的服務，請使用 &lt;httpRuntime targetFramework=&quot;x.x&quot; /&gt; 項目，將目標設為舊版 .NET Framework。</li><li>將下列行新增至 app.config 檔案中的 <code>&lt;appSettings&gt;</code> 區段：<code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|範圍|次要|
|版本|4.6|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|

