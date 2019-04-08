---
title: Visual Studio 2012 的識別和存取工具
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
ms.openlocfilehash: 9216298889637780e79d1bfc7ac060458c745968
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170114"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a><span data-ttu-id="55033-102">Visual Studio 2012 的識別和存取工具</span><span class="sxs-lookup"><span data-stu-id="55033-102">Identity and Access Tool for Visual Studio 2012</span></span>
<span data-ttu-id="55033-103">本主題說明適用於 Visual Studio 11 的新識別和存取工具。</span><span class="sxs-lookup"><span data-stu-id="55033-103">This topic describes the new Identity and Access Tool for Visual Studio 11.</span></span> <span data-ttu-id="55033-104">您可以從下列 URL 下載此工具： [ https://go.microsoft.com/fwlink/?LinkID=245849 ](https://go.microsoft.com/fwlink/?LinkID=245849)或直接從 Visual Studio 11，藉由搜尋 「 識別 」，直接在延伸模組管理員中。</span><span class="sxs-lookup"><span data-stu-id="55033-104">You can download this tool from the following URL: [https://go.microsoft.com/fwlink/?LinkID=245849](https://go.microsoft.com/fwlink/?LinkID=245849) or directly from within Visual Studio 11 by searching for "identity" directly in the Extensions Manager.</span></span>  
  
 <span data-ttu-id="55033-105">適用於 Visual Studio 11 的新識別和存取工具具有下列優點，可大幅簡化開發時間：</span><span class="sxs-lookup"><span data-stu-id="55033-105">The Identity and Access Tool for Visual Studio 11 delivers a dramatically simplified development-time experience with the following highlights:</span></span>  
  
-   <span data-ttu-id="55033-106">使用這項新工具，您可以使用 Web 應用程式專案類型並以 IIS Express 為目標進行開發。</span><span class="sxs-lookup"><span data-stu-id="55033-106">Using the new tool, you can develop using web applications project types and target IIS express.</span></span>  
  
-   <span data-ttu-id="55033-107">這項新工具與僅具有保護功能的驗證方式不同，您可以指定本機主領域探索頁面/控制站 (或是在應用程式中處理驗證經驗的其他端點)，而 WIF 會將所有未驗證的要求都設定為移至該頁面/控制站，而不是將這些頁面重新導向至 STS。</span><span class="sxs-lookup"><span data-stu-id="55033-107">Unlike with the blanket protection-only authentication, with the new tool, you can specify your local home realm discovery page/controller (or any other endpoint handling the authentication experience within your application) and WIF will configure all unauthenticated requests to go there, instead of redirecting them to the STS.</span></span>  
  
-   <span data-ttu-id="55033-108">此工具包含測試 Security Token Service (STS)，當您啟動偵錯工作階段時，STS 隨即在您的本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="55033-108">The tool includes a test Security Token Service (STS) which runs on your local machine when you launch a debug session.</span></span> <span data-ttu-id="55033-109">因此，您不必再建立自訂和調整 STS 專案，就可以取得測試應用程式所需的宣告。</span><span class="sxs-lookup"><span data-stu-id="55033-109">Therefore, you no longer need to create custom STS projects and tweak them in order to get the claims you need to test your applications.</span></span> <span data-ttu-id="55033-110">宣告類型和值都開放完全自訂。</span><span class="sxs-lookup"><span data-stu-id="55033-110">The claim types and values are fully customizable.</span></span>  
  
-   <span data-ttu-id="55033-111">您可以直接透過工具的 UI 修改一般設定，而不必編輯 web.config。</span><span class="sxs-lookup"><span data-stu-id="55033-111">You can modify common settings directly via the tool’s UI, without the need to edit web.config.</span></span>  
  
-   <span data-ttu-id="55033-112">您可以在單一螢幕中，利用 Active Directory Federation Services (AD FS) 2.0 (或其他 WS-Federation 提供者) 建立同盟。</span><span class="sxs-lookup"><span data-stu-id="55033-112">You can establish federation with Active Directory Federation Services (AD FS) 2.0 (or other WS-Federation providers) in a single screen.</span></span>  
  
-   <span data-ttu-id="55033-113">此工具會利用簡單的核取方塊清單的 Windows Azure 存取控制服務 (ACS) 功能，您想要使用的所有身分識別提供者：Facebook、 Google、 Live ID、 yahoo ！、 所有 OpenID 提供者和任何 WS-同盟提供者。</span><span class="sxs-lookup"><span data-stu-id="55033-113">The tool leverages Windows Azure Access Control Service (ACS) capabilities with a simple list of checkboxes for all the identity providers that you want to use: Facebook, Google, Live ID, Yahoo!, any OpenID provider, and any WS-Federation provider.</span></span> <span data-ttu-id="55033-114">只要選取識別提供者、按一下 [確定]，然後按 F5，您的應用程式和 ACS 即可自動設定完成，成為 ACS 感知測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="55033-114">Select your identity providers, click OK, then F5, and both your application and ACS will be automatically configured and your test application will be ACS-aware.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55033-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55033-115">See also</span></span>

- [<span data-ttu-id="55033-116">WIF 功能</span><span class="sxs-lookup"><span data-stu-id="55033-116">WIF Features</span></span>](../../../docs/framework/security/wif-features.md)
