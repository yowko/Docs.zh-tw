---
ms.openlocfilehash: 12ba3bd3c9e9e00b88cab0e568a1ce0f4f8bbb05
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606439"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a><span data-ttu-id="76eb9-101">CspParameters.ParentWindowHandle 現在預期有 HWND 值</span><span class="sxs-lookup"><span data-stu-id="76eb9-101">CspParameters.ParentWindowHandle now expects HWND value</span></span>

#### <a name="details"></a><span data-ttu-id="76eb9-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="76eb9-102">Details</span></span>

<span data-ttu-id="76eb9-103">.NET Framework 2.0 中引進的 <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> 值，可讓應用程式註冊父視窗控制代碼值，因而存取金鑰所需的任何 UI (如 PIN 提示或同意對話方塊) 在指定的視窗會開啟為強制回應子項。從以 .NET Framework 4.7 為目標的應用程式開始，Windows Forms 應用程式可以使用如下的程式碼設定 <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> 屬性：</span><span class="sxs-lookup"><span data-stu-id="76eb9-103">The <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> value, introduced in .NET Framework 2.0, allows an application to register a parent window handle value such that any UI required to access the key (such as a PIN prompt or consent dialog) opens as a modal child to the specified window.Starting with apps that target the .NET Framework 4.7, a Windows Forms application can set the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> property with code like the following:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="76eb9-104">在舊版 .NET Framework 中，值必須為 <xref:System.IntPtr?displayProperty=fullName>，代表存放 [HWND](/windows/desktop/WinProg/windows-data-types#HWND) 值之記憶體中的位置。</span><span class="sxs-lookup"><span data-stu-id="76eb9-104">In previous versions of the .NET Framework, the value was expected to be an <xref:System.IntPtr?displayProperty=fullName> representing a location in memory where the [HWND](/windows/desktop/WinProg/windows-data-types#HWND) value resided.</span></span> <span data-ttu-id="76eb9-105">在 Windows 7 和舊版中，將屬性設為 form.Handle 不會有任何作用，但在 Windows 8 和更新的版本中，則會導致 &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>：參數不正確。&quot;</span><span class="sxs-lookup"><span data-stu-id="76eb9-105">Setting the property to form.Handle on Windows 7 and earlier versions had no effect, but on Windows 8 and later versions, it results in a &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>: The parameter is incorrect.&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="76eb9-106">建議</span><span class="sxs-lookup"><span data-stu-id="76eb9-106">Suggestion</span></span>

<span data-ttu-id="76eb9-107">以 .NET Framework 4.7 或更新版本為目標的應用程式若要註冊父視窗關聯性，建議使用以下的簡化格式︰</span><span class="sxs-lookup"><span data-stu-id="76eb9-107">Applications targeting .NET Framework 4.7 or higher wishing to register a parent window relationship are encouraged to use the simplified form:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="76eb9-108">使用者如已發現要傳遞的正確值，是 `form.Handle` 值所在之記憶體位置的位址，則可以藉由將 AppContext 參數 `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` 設為 `true` 以選擇退出行為變更：</span><span class="sxs-lookup"><span data-stu-id="76eb9-108">Users who had identified that the correct value to pass was the address of a memory location which held the value `form.Handle` can opt out of the behavior change by setting the AppContext switch `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` to `true`:</span></span>

- <span data-ttu-id="76eb9-109">以程式設計方式設定 AppContext 的相容性參數，如[這裡](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)所述。</span><span class="sxs-lookup"><span data-stu-id="76eb9-109">By programmatically setting compat switches on the AppContext, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="76eb9-110">將下列程式行加入至 app.config 檔案的 `<runtime>` 區段：</span><span class="sxs-lookup"><span data-stu-id="76eb9-110">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<runtime>
 <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
</runtime>
```

<span data-ttu-id="76eb9-111">相反地，若使用者想在應用程式在舊版 .NET Framework 下載入時，選擇加入 .NET Framework 4.7 執行階段上的新行為，可以將 AppContext 參數設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="76eb9-111">Conversely, users who wish to opt in to the new behavior on the .NET Framework 4.7 runtime when the application loads under older .NET Framework versions can set the AppContext switch to `false`.</span></span>

| <span data-ttu-id="76eb9-112">名稱</span><span class="sxs-lookup"><span data-stu-id="76eb9-112">Name</span></span>    | <span data-ttu-id="76eb9-113">值</span><span class="sxs-lookup"><span data-stu-id="76eb9-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="76eb9-114">範圍</span><span class="sxs-lookup"><span data-stu-id="76eb9-114">Scope</span></span>   | <span data-ttu-id="76eb9-115">Minor</span><span class="sxs-lookup"><span data-stu-id="76eb9-115">Minor</span></span>       |
| <span data-ttu-id="76eb9-116">版本</span><span class="sxs-lookup"><span data-stu-id="76eb9-116">Version</span></span> | <span data-ttu-id="76eb9-117">4.7</span><span class="sxs-lookup"><span data-stu-id="76eb9-117">4.7</span></span>         |
| <span data-ttu-id="76eb9-118">類型</span><span class="sxs-lookup"><span data-stu-id="76eb9-118">Type</span></span>    | <span data-ttu-id="76eb9-119">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="76eb9-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="76eb9-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="76eb9-120">Affected APIs</span></span>

- <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType>
