---
title: "風險降低︰MemberDescriptor.Equals"
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
ms.assetid: cf3735f0-0dd4-4bef-b4b0-575264e10f39
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4989d3c2611b500063158955f102931902e1ab32
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-memberdescriptorequals"></a><span data-ttu-id="621cd-102">風險降低︰MemberDescriptor.Equals</span><span class="sxs-lookup"><span data-stu-id="621cd-102">Mitigation: MemberDescriptor.Equals</span></span>
<span data-ttu-id="621cd-103">從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法的實作已經變更。</span><span class="sxs-lookup"><span data-stu-id="621cd-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the implementation of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method has changed.</span></span> <span data-ttu-id="621cd-104">因為 `System.ComponentModel.EventDescriptor.Equals` 和 `System.ComponentModel.PropertyDescriptor.Equals` 方法繼承基底類別實作，所以變更也會影響這些方法。</span><span class="sxs-lookup"><span data-stu-id="621cd-104">Because the `System.ComponentModel.EventDescriptor.Equals` and  `System.ComponentModel.PropertyDescriptor.Equals` methods inherit the base class implementation, the change also affects these methods.</span></span>  
  
 <span data-ttu-id="621cd-105">在以 .NET Framework [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 之前的版本為目標的應用程式中，<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法的相等測試部分會不正確地比較某個物件的 <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> 屬性與另一個物件的 <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> 屬性。</span><span class="sxs-lookup"><span data-stu-id="621cd-105">In apps that target versions of the .NET Framework prior to [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a portion of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method's test for equality  incorrectly compared the <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> property of one object with the <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> property of the other.</span></span> <span data-ttu-id="621cd-106">從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法會比較兩個物件的 <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> 屬性。</span><span class="sxs-lookup"><span data-stu-id="621cd-106">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method compares the <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> property of the two objects.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="621cd-107">影響</span><span class="sxs-lookup"><span data-stu-id="621cd-107">Impact</span></span>  
 <span data-ttu-id="621cd-108">這項變更會正確地實作 <xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> 物件的相等測試，而且影響應該最低。</span><span class="sxs-lookup"><span data-stu-id="621cd-108">This change correctly implements the test for equality for <xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> objects and should have minimal impact.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="621cd-109">緩和</span><span class="sxs-lookup"><span data-stu-id="621cd-109">Mitigation</span></span>  
 <span data-ttu-id="621cd-110">如果您的應用程式是以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 或更新版本的 .NET Framework 為目標，並相依於有時在成員描述項相等時會傳回 `false` 的 <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法，可採取下列兩種因應措施：</span><span class="sxs-lookup"><span data-stu-id="621cd-110">Two workarounds are available if your app targets the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or a later version of the .NET Framework and it depends on the  <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method sometimes returning `false` when member descriptors are equivalent:</span></span>  
  
-   <span data-ttu-id="621cd-111">您可以將下列內容加入至 app.config 檔案的 [\<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，以選擇退出這項變更而不修改您的原始程式碼：</span><span class="sxs-lookup"><span data-stu-id="621cd-111">You can opt out of this change without modifying your source code by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value = "Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />  
     </runtime>  
    ```  
  
-   <span data-ttu-id="621cd-112">呼叫 <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法之後，您可以修改原始程式碼來還原舊有行為，方法是手動比較 <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> 與 <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> 屬性，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="621cd-112">You can modify your source code to restore the previous behavior by manually comparing the  <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> and <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> properties after calling the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> method, as the following code fragment does.</span></span>  
  
    ```csharp  
    if (memberDescriptor1.Equals(memberDescriptor2) &   
        memberDescriptor1.Description.Equals(memberDescriptor2.Category)) {  
          // Code to execute if true.  
    }  
    else {  
          // Code to execute if false.     
    }  
    ```  
  
    ```  
    If memberDescriptor1.Equals(memberDescriptor2) And   
        memberDescriptor1.Description.Equals(memberDescriptor2.Category)  
          // Code to execute if True.  
    Else  
          // Code to execute if False.     
    End If  
    ```  
  
 <span data-ttu-id="621cd-113">對於以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和舊版本為目標的應用程式，您可以在 app.config 檔案中加入下列值以啟用這項變更︰</span><span class="sxs-lookup"><span data-stu-id="621cd-113">For apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, you can enable this change by adding the following value to your app.config file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="621cd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="621cd-114">See Also</span></span>  
 <span data-ttu-id="621cd-115">[重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md) </span><span class="sxs-lookup"><span data-stu-id="621cd-115">[Retargeting Changes](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md) </span></span>  
 [<span data-ttu-id="621cd-116">4.6.2 中的應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="621cd-116">Application Compatibility in 4.6.2</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)

