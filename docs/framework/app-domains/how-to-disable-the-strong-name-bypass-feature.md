---
title: "如何：停用強式名稱略過功能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "強式名稱略過功能"
  - "強式名稱組件，載入至受信任的應用程式定義域"
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
caps.latest.revision: 30
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 30
---
# 如何：停用強式名稱略過功能
從 .NET Framework 3.5 版 Service Pack 1 \(SP1\) 開始，將組件載入至完全信任的 <xref:System.AppDomain> 物件 \(例如 `MyComputer` 區域的預設 <xref:System.AppDomain>\) 時，不會驗證強式名稱 \(Strong Name\) 簽章。  這稱為強式名稱略過功能。  在完全信任的環境中，已簽署、完全信任的組件 \(Assembly\) 要求 <xref:System.Security.Permissions.StrongNameIdentityPermission> 永遠會成功，不論其簽章為何。  唯一的限制是組件必須完全受信任，因為它的區域是完全受信任的。  在這些情況下，由於強式名稱並非決定性因素，因此沒有必要進行驗證。  略過強式名稱簽章的驗證可大幅提升效能。  
  
 略過功能會套用至任何未延遲簽署的完全信任組件，以及從其 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性所指定之目錄載入至任何完全信任 <xref:System.AppDomain> 的完全信任組件。  
  
 您可以設定登錄機碼值，為電腦上的所有應用程式覆寫略過功能。  若要覆寫單一應用程式的設定，則可以使用應用程式的組態檔。  如果已經透過登錄機碼停用略過功能，則無法為單一應用程式重新啟用略過功能。  
  
 當您覆寫略過功能時，系統只會驗證強式名稱是否正確，而不會檢查 <xref:System.Security.Permissions.StrongNameIdentityPermission>。  如果您要確認特定的強式名稱，則必須另外執行檢查。  
  
> [!IMPORTANT]
>  強制強式名稱驗證的能力會根據登錄機碼而定，如下列程序所述。  如果執行應用程式的帳戶沒有存取控制清單 \(ACL\) 使用權限來存取該登錄機碼，設定就無效。  您必須確定此機碼已經設定 ACL 權限，所有組件都可以讀取它。  
  
### 若要停用所有應用程式的強式名稱略過功能  
  
-   在 32 位元電腦上系統登錄的 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework 機碼底下，建立值為 0 且名稱為 `AllowStrongNameBypass` 的 DWORD 項目。  
  
-   在 64 位元電腦上系統登錄的 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework 和 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework 機碼底下，建立值為 0 且名稱為 `AllowStrongNameBypass` 的 DWORD 項目。  
  
### 若要停用單一應用程式的強式名稱略過功能  
  
1.  開啟或建立應用程式組態檔。  
  
     如需這個檔案的詳細資訊，請參閱[設定應用程式](../../../docs/framework/configure-apps/index.md)中的＜應用程式組態檔＞一節。  
  
2.  加入下列項目：  
  
    ```  
    <configuration>  
      <runtime>  
         < bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 您可以移除組態檔設定或將屬性 \(Attribute\) 設定為 "true"，藉此還原應用程式的略過功能。  
  
> [!NOTE]
>  只有在電腦啟用略過功能時，您才能開啟和關閉應用程式的強式名稱驗證。  如果電腦關閉略過功能，則所有應用程式都必須驗證強式名稱，並且您無法設定單一應用程式略過驗證。  
  
## 請參閱  
 [Sn.exe \(Strong Name Tool\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [\<bypassTrustedAppStrongNames\> 項目](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)   
 [建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)