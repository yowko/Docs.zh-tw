---
title: "授權存取服務作業 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "授權, Windows Communication Foundation 範例"
  - "授權存取服務作業範例 [Windows Communication Foundation]"
  - "服務行為, 授權存取範例"
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# 授權存取服務作業
這個範例會示範如何使用 [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)，以便利用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 屬性來授權存取服務作業。  這個範例是以[使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)範例為基礎。  服務與用戶端是使用 [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)完成設定。  [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)的 `mode` 屬性已經設定為 `Message`，而 `clientCredentialType` 已經設定為 `Windows`。  <xref:System.Security.Permissions.PrincipalPermissionAttribute> 會套用至每個服務方法，並且用來限制每個作業的存取。  呼叫者必須是 Windows 系統管理員才能存取每個作業。  
  
 在這個範例中，用戶端是主控台應用程式 \(.exe\)，而服務則是由網際網路資訊服務 \(IIS\) 所裝載。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 服務組態檔會使用 [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)來設定 `principalPermissionMode` 屬性：  
  
```  
<behaviors>  
  <serviceBehaviors>  
    <behavior>  
      ...  
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
  
```  
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。  如果用戶端是以 Administrators 群組成員的帳戶執行，該用戶端便能與每個作業進行成功通訊，否則就會拒絕存取。  為了體驗授權失敗，這時要使用不屬於 Administrators 群組的帳戶來執行用戶端。  在主控台視窗中按 ENTER 鍵，即可關閉用戶端。  
  
 藉由實作 <xref:System.ServiceModel.Dispatcher.IErrorHandler>，即可向服務通知授權失敗。  如需實作 `IErrorHandler` 的詳細資訊，請參閱[延伸對錯誤處理和報告的控制](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)。  
  
### 若要安裝、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
## 請參閱