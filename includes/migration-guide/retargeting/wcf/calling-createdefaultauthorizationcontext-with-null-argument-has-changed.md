---
ms.openlocfilehash: c5a061dffa1deb66e1769d6ec70dfa2155ac6a31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615627"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>使用 Null 引數呼叫 CreateDefaultAuthorizationContext 已變更

#### <a name="details"></a>詳細資料

使用 Null authorizationPolicies 引數呼叫 <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> 所傳回的 <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> 實作，已變更其在 .NET Framework 4.6 中的實作。

#### <a name="suggestion"></a>建議

在少數情況下，使用自訂驗證的 WCF 應用程式，在行為上可能會有些許差異。 在此情況下，您可使用下列兩種方式之一還原舊版行為：

- 以 .NET Framework 4.6 之前的舊版為目標，重新編譯您的應用程式。 對於裝載在 IIS 上的服務，請使用 `<httpRuntime targetFramework="x.x">` 項目，將目標設為舊版 .NET Framework。
- 將下列行加入 app.config 檔案中的 `<appSettings>` 區段：

    ```xml
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />
    ```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.6         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType>
