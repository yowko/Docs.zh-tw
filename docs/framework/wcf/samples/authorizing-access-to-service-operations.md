---
title: 授權存取服務作業
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: a0ea82c876b3bd8c2a3218f84399fbb69e1d0080
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932502"
---
# <a name="authorizing-access-to-service-operations"></a>授權存取服務作業
這個範例示範如何使用[ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)來<xref:System.Security.Permissions.PrincipalPermissionAttribute>啟用屬性的使用, 以授權存取服務作業。 這個範例是以[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)範例為基礎。 服務和用戶端是使用[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)來設定。 `Message` `clientCredentialType` `Windows`[安全性>\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)的`mode`屬性已設定為, 而且已設定為。 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 會套用至每個服務方法，並且用來限制每個作業的存取。 呼叫者必須是 Windows 系統管理員才能存取每個作業。  
  
 在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 服務設定檔會使用[ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)來設定`principalPermissionMode`屬性:  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>   
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 將 `principalPermissionMode` 設定為 `UseWindowsGroups`，便可以根據 Windows 群組名稱來使用 <xref:System.Security.Permissions.PrincipalPermissionAttribute>。  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 會套用至每個作業以要求呼叫者必須是 Windows Administrators 群組的成員，如下列範例程式碼所示。  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 如果用戶端是以 Administrators 群組成員的帳戶執行，該用戶端便能與每個作業進行成功通訊，否則就會拒絕存取。 為了體驗授權失敗，這時要使用不屬於 Administrators 群組的帳戶來執行用戶端。 在主控台視窗中按 ENTER 鍵，即可關閉用戶端。  
  
 藉由實作 <xref:System.ServiceModel.Dispatcher.IErrorHandler>，即可向服務通知授權失敗。 如需有關執行`IErrorHandler`的資訊, 請參閱[擴充對錯誤處理和報告的控制](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
