---
title: "風險降低︰ClaimsIdentity 建構函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 946903f1-0fbf-4f67-805b-1eb48352024d
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a50cbd69aa1f2c72adc9fc4d10a070f5faa0cf54
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-claimsidentity-constructor"></a><span data-ttu-id="a8e58-102">風險降低︰ClaimsIdentity 建構函式</span><span class="sxs-lookup"><span data-stu-id="a8e58-102">Mitigation: ClaimsIdentity Constructor</span></span>
<span data-ttu-id="a8e58-103">從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，已變更 <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> 建構函式如何設定 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a8e58-103">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], there is change in how the <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> constructor sets the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> property.</span></span> <span data-ttu-id="a8e58-104">如果 <xref:System.Security.Principal.IIdentity> 引數是 <xref:System.Security.Claims.ClaimsIdentity> 物件，而且該 <xref:System.Security.Claims.ClaimsIdentity> 物件的 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> 屬性不是 `null`，則會使用 <xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName> 方法來附加 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a8e58-104">If the <xref:System.Security.Principal.IIdentity> argument is a <xref:System.Security.Claims.ClaimsIdentity> object, and the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> property of that <xref:System.Security.Claims.ClaimsIdentity> object is not `null`, the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> property is attached by using the <xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="a8e58-105">在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中，<xref:System.Security.Claims.ClaimsIdentity.Actor%2A> 屬性會附加為現有參考。</span><span class="sxs-lookup"><span data-stu-id="a8e58-105">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> property is attached as a  existing reference.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="a8e58-106">影響</span><span class="sxs-lookup"><span data-stu-id="a8e58-106">Impact</span></span>  
 <span data-ttu-id="a8e58-107">從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，新 <xref:System.Security.Claims.ClaimsIdentity> 物件的 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> 屬性不等於建構函式之 <xref:System.Security.Principal.IIdentity> 引數的 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a8e58-107">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> property of the new <xref:System.Security.Claims.ClaimsIdentity> object is not equal to the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> property of the constructor's <xref:System.Security.Principal.IIdentity> argument.</span></span> <span data-ttu-id="a8e58-108">在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和先前的版本中則是相等的。</span><span class="sxs-lookup"><span data-stu-id="a8e58-108">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, it is equal.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="a8e58-109">緩和</span><span class="sxs-lookup"><span data-stu-id="a8e58-109">Mitigation</span></span>  
 <span data-ttu-id="a8e58-110">如果不想要這種行為，您可以將應用程式組態檔中的 `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` 參數設為 `true` 來還原舊版行為。</span><span class="sxs-lookup"><span data-stu-id="a8e58-110">If this behavior is undesirable, you can restore the previous behavior by setting the `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` switch in your application configuration file to `true`.</span></span> <span data-ttu-id="a8e58-111">您會需要將下列內容加入 web.config 檔案的 [\<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段︰</span><span class="sxs-lookup"><span data-stu-id="a8e58-111">This requires that you add the following to  the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your web.config file:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8e58-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8e58-112">See Also</span></span>  
 [<span data-ttu-id="a8e58-113">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="a8e58-113">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

