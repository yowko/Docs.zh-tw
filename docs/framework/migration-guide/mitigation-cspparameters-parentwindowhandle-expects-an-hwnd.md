---
title: "風險降低︰CspParameters.ParentWindowHandle 應該有 HWND"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- CspParameters.ParentWindowHandle
- CspParameters.ParentWindowHandle retargeting change
ms.assetid: 33264333-71d6-4d43-8827-9c98878cfea7
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1b65aaf7149ca29b2af3efdf44ee9489a04c73a2
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-cspparametersparentwindowhandle-expects-an-hwnd"></a><span data-ttu-id="fe974-102">風險降低︰CspParameters.ParentWindowHandle 應該有 HWND</span><span class="sxs-lookup"><span data-stu-id="fe974-102">Mitigation: CspParameters.ParentWindowHandle Expects an HWND</span></span>

<span data-ttu-id="fe974-103">.NET Framework 2.0 中引進的 <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> 屬性可讓應用程式註冊父視窗控制代碼值，因而存取金鑰所需的任何 UI (如 PIN 提示或同意對話方塊) 在指定的視窗會開啟為強制回應子項。</span><span class="sxs-lookup"><span data-stu-id="fe974-103">The <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> property, introduced in the .NET Framework 2.0, allows an application to register a parent window handle value such that any UI required to access the key (such as a PIN prompt or a consent dialog) opens as a modal child to the specified window.</span></span> <span data-ttu-id="fe974-104">從以 .NET Framework 4.7 為目標的應用程式開始，可以將視窗控制代碼 (HWND) 指派給這個屬性。</span><span class="sxs-lookup"><span data-stu-id="fe974-104">Starting with applications that target the .NET Framework 4.7, a window handle (HWND) can be assigned to this property.</span></span>

<span data-ttu-id="fe974-105">在 .NET Framework 4.6.2 (含) 以前的 .NET Framework 版本中，指派給 <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> 屬性的值必須是 <xref:System.IntPtr>，其表示 HWND 值在記憶體中的所在位置。</span><span class="sxs-lookup"><span data-stu-id="fe974-105">In versions of the .NET Framework through the .NET Framework 4.6.2, the value assigned to the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> property was expected to be an <xref:System.IntPtr> that represents the location in memory where the HWND value resided.</span></span> <span data-ttu-id="fe974-106">在 Windows 7 和舊版的 Windows 作業系統中，將該屬性設為 `form.Handle` 不會有任何作用，但在 Windows 8 和更新的版本中，則會導致 <xref:System.Security.Cryptography> 並顯示「參數不正確」訊息。</span><span class="sxs-lookup"><span data-stu-id="fe974-106">On Windows 7 and earlier versions of the Windows operating system, setting the property to `form.Handle` had no effect, but on Windows 8 and later versions, it results in a <xref:System.Security.Cryptography> with the message, "The parameter is incorrect."</span></span>

<span data-ttu-id="fe974-107">從以 .NET Framework 4.7 為目標的應用程式開始，Windows Forms 應用程式可透過以下的程式碼設定 <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> 屬性：</span><span class="sxs-lookup"><span data-stu-id="fe974-107">Starting with apps that target the .NET Framework 4.7, a Windows Forms application can set the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> property with code like the following:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="impact"></a><span data-ttu-id="fe974-108">影響</span><span class="sxs-lookup"><span data-stu-id="fe974-108">Impact</span></span>

<span data-ttu-id="fe974-109">以 .NET Framework 4.7 或更新版本為目標的應用程式若要註冊父視窗關聯性，建議使用以下的簡化格式︰</span><span class="sxs-lookup"><span data-stu-id="fe974-109">Applications targeting the .NET Framework 4.7 or later that wish to register a parent window relationship are encouraged to use the simplified form:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="mitigation"></a><span data-ttu-id="fe974-110">緩和</span><span class="sxs-lookup"><span data-stu-id="fe974-110">Mitigation</span></span>

<span data-ttu-id="fe974-111">開發人員如已發現正確值是 `form.Handle` 值所在之記憶體位置的位址，可以藉由將 <xref:System.AppContext> 參數 `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` 設為 `true` 以退出此行為變更：</span><span class="sxs-lookup"><span data-stu-id="fe974-111">Developers who had identified that the correct value was the address of the memory location that held the `form.Handle` value can opt out of this change in behavior by setting the <xref:System.AppContext> switch `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` to `true`:</span></span>

- <span data-ttu-id="fe974-112">以程式設計方式設定 <xref:System.AppContext> 執行個體上的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="fe974-112">By programmatically setting compatibility switches on the <xref:System.AppContext> instance.</span></span>

- <span data-ttu-id="fe974-113">將下列程式行加入至 app.config 檔案的 `<runtime>` 區段：</span><span class="sxs-lookup"><span data-stu-id="fe974-113">By adding the following line to the `<runtime>` section of the app.config file:</span></span>
   
   ```xml
   <runtime>
     <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
   </runtime>
   ```

<span data-ttu-id="fe974-114">相反地，若使用者想針對執行 .NET Framework 4.7 但以舊版 .NET Framework 為目標的應用程式加入新的行為，可以將 <xref:System.AppContext> 參數設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="fe974-114">Conversely, users who wish to opt in to the new behavior for applications that run under the .NET Framework 4.7 but target an earlier version of the .NET Framework versions can set the <xref:System.AppContext> switch to `false`.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="fe974-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe974-115">See also</span></span>

[<span data-ttu-id="fe974-116">.NET Framework 4.7 中的重定目標變更</span><span class="sxs-lookup"><span data-stu-id="fe974-116">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

