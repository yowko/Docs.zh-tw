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
# <a name="mitigation-memberdescriptorequals"></a>風險降低︰MemberDescriptor.Equals
從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法的實作已經變更。 因為 `System.ComponentModel.EventDescriptor.Equals` 和 `System.ComponentModel.PropertyDescriptor.Equals` 方法繼承基底類別實作，所以變更也會影響這些方法。  
  
 在以 .NET Framework [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 之前的版本為目標的應用程式中，<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法的相等測試部分會不正確地比較某個物件的 <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> 屬性與另一個物件的 <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> 屬性。 從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法會比較兩個物件的 <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> 屬性。  
  
## <a name="impact"></a>影響  
 這項變更會正確地實作 <xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> 物件的相等測試，而且影響應該最低。  
  
## <a name="mitigation"></a>緩和  
 如果您的應用程式是以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 或更新版本的 .NET Framework 為目標，並相依於有時在成員描述項相等時會傳回 `false` 的 <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法，可採取下列兩種因應措施：  
  
-   您可以將下列內容加入至 app.config 檔案的 [\<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，以選擇退出這項變更而不修改您的原始程式碼：  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value = "Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />  
     </runtime>  
    ```  
  
-   呼叫 <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法之後，您可以修改原始程式碼來還原舊有行為，方法是手動比較 <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> 與 <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> 屬性，如下列程式碼片段所示。  
  
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
  
 對於以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和舊版本為目標的應用程式，您可以在 app.config 檔案中加入下列值以啟用這項變更︰  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true />  
</runtime>  
```  
  
## <a name="see-also"></a>另請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)   
 [4.6.2 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)

