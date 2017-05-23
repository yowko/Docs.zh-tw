---
title: "風險降低︰MemberDescriptor.Equals | Microsoft Docs"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 409f06f4dfbe7be50dd2c487e49d3d4d8a477539
ms.contentlocale: zh-tw
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-memberdescriptorequals"></a>風險降低︰MemberDescriptor.Equals
從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法的實作已變更。 因為 `System.ComponentModel.EventDescriptor.Equals` 和 `System.ComponentModel.PropertyDescriptor.Equals` 方法繼承基底類別實作，所以變更也會影響這些方法。  
  
 在以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以前的 .NET Framework 版本為目標的應用程式中，部分<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法的相等測試會不當地比較一個物件的 <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> 屬性和另一個物件的 <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> 屬性。 從以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標的應用程式開始，<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法會比較兩個物件的 <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> 屬性。  
  
## <a name="impact"></a>影響  
 這項變更可正確實作 <xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> 物件的相等測試，且影響極小。  
  
## <a name="mitigation"></a>緩和  
 如果您的應用程式是以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 或更新版本的 .NET Framework 為目標，並相依於有時在成員描述元相等時會傳回 `false` 的 <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法，可採取下列兩種因應措施：  
  
-   您可以將下列內容加入至 app.config 檔案的 [\<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，以選擇退出這項變更而不修改您的原始程式碼：  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value = "Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />  
     </runtime>  
    ```  
  
-   您可以修改原始程式碼以還原舊版的行為，方法是在呼叫 <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> 方法後，透過手動方式來比較 <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> 與 <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> 屬性，如以下的程式碼片段所示。  
  
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

