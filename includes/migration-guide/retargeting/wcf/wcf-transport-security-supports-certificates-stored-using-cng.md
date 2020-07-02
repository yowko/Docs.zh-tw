---
ms.openlocfilehash: 5c09bee92f679cd7e7a95cd23d5ce0ca9b57170c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614357"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a><span data-ttu-id="a0f32-101">WCF 傳輸安全性支援使用 CNG 儲存的憑證</span><span class="sxs-lookup"><span data-stu-id="a0f32-101">WCF transport security supports certificates stored using CNG</span></span>

#### <a name="details"></a><span data-ttu-id="a0f32-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a0f32-102">Details</span></span>

<span data-ttu-id="a0f32-103">從以 .NET Framework 4.6.2 為目標的應用程式開始，WCF 傳輸安全性支援使用 Windows 密碼編譯程式庫 (CNG) 儲存的憑證。</span><span class="sxs-lookup"><span data-stu-id="a0f32-103">Starting with apps that target the .NET Framework 4.6.2, WCF transport security supports certificates stored using the Windows Cryptography Library (CNG).</span></span> <span data-ttu-id="a0f32-104">這項支援僅限於具有公開金鑰的憑證，且指數長度不能超過 32 位元。</span><span class="sxs-lookup"><span data-stu-id="a0f32-104">This support is limited to certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="a0f32-105">當應用程式以 .NET Framework 4.6.2 為目標時，此功能預設為開啟。在舊版 .NET Framework 中，嘗試搭配 CSG 金鑰儲存提供者使用 X509 憑證會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a0f32-105">When an application targets the .NET Framework 4.6.2, this feature is on by default.In earlier versions of the .NET Framework, the attempt to use X509 certificates with a CSG key storage provider throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a0f32-106">建議</span><span class="sxs-lookup"><span data-stu-id="a0f32-106">Suggestion</span></span>

<span data-ttu-id="a0f32-107">應用程式是以 .NET Framework 4.6.1 和更早版本為目標，但卻執行於 .NET Framework 4.6.2 當中，則可將下列這一行新增至 app.config 或 web.config 檔的 `<runtime>` 區段，來啟用支援 CNG 憑證：</span><span class="sxs-lookup"><span data-stu-id="a0f32-107">Apps that target the .NET Framework 4.6.1 and earlier but are running on the .NET Framework 4.6.2 can enable support for CNG certificates by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableCngCertificates=false" />
</runtime>
```

<span data-ttu-id="a0f32-108">這也可以用程式設計方式，以下列程式碼完成︰</span><span class="sxs-lookup"><span data-stu-id="a0f32-108">This can also be done programmatically with the following code:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate";

AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="a0f32-109">請注意，由於這項變更，將不再執行任何倚賴使用 CNG 憑證嘗試起始安全通訊失敗的任何例外住況處理程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0f32-109">Note that, because of this change, any exception handling code that depends on the attempt to initiate secure communication with a CNG certificate to fail will no longer execute.</span></span>

| <span data-ttu-id="a0f32-110">名稱</span><span class="sxs-lookup"><span data-stu-id="a0f32-110">Name</span></span>    | <span data-ttu-id="a0f32-111">值</span><span class="sxs-lookup"><span data-stu-id="a0f32-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a0f32-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="a0f32-112">Scope</span></span>   | <span data-ttu-id="a0f32-113">Minor</span><span class="sxs-lookup"><span data-stu-id="a0f32-113">Minor</span></span>       |
| <span data-ttu-id="a0f32-114">版本</span><span class="sxs-lookup"><span data-stu-id="a0f32-114">Version</span></span> | <span data-ttu-id="a0f32-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="a0f32-115">4.6.2</span></span>       |
| <span data-ttu-id="a0f32-116">類型</span><span class="sxs-lookup"><span data-stu-id="a0f32-116">Type</span></span>    | <span data-ttu-id="a0f32-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="a0f32-117">Retargeting</span></span> |
