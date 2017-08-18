---
title: "如何：停用強式名稱略過功能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
caps.latest.revision: 30
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0af565c6d27be6a5a22bfb0fd1f90e4e46deec33
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>如何：停用強式名稱略過功能
從 .NET Framework 3.5 版 Service Pack 1 (SP1) 開始，當組件載入到完全信任的 <xref:System.AppDomain> 物件 (例如適用於 `MyComputer` 區域的預設 <xref:System.AppDomain>) 時，不會驗證強式名稱簽章。 這是指強式名稱略過功能。 在完全信任環境中，不論簽章為何，已簽署、完全信任的組件要求 <xref:System.Security.Permissions.StrongNameIdentityPermission> 一律會成功。 唯一的限制是組件必須是完全受信任的，因為它的區域是完全信任的。 因為強式名稱不是這些情況下的決定因素，所以不需要進行驗證。 略過強式名稱簽章驗證可大幅提升效能。  
  
 略過功能適用於任何完全信任的組件，該組件非延遲簽署，且已從其 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性指定的目錄載入至所有完全信任的 <xref:System.AppDomain>。  
  
 您可以設定登錄機碼值，覆寫電腦上所有應用程式的略過功能。 您可以使用應用程式組態檔覆寫單一應用程式的設定。 如果登錄機碼已停用該功能，您即無法恢復單一應用程式的略過功能。  
  
 當您覆寫略過功能時，只會驗證強式名稱的正確性，不檢查 <xref:System.Security.Permissions.StrongNameIdentityPermission>。 如果您想要確認特定的強式名稱，您必須另外執行檢查。  
  
> [!IMPORTANT]
>  能否強制執行強式名稱驗證，視登錄機碼而定，如下列程序所述。 如果在沒有存取控制清單 (ACL) 權限的帳戶下，執行應用程式存取該登錄機碼，則設定為無效。 您必須確定此機碼已設定 ACL 權限，它才能為所有組件讀取。  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a>停用所有應用程式的強式名稱略過功能  
  
-   在 32 位元電腦系統登錄的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 機碼下，建立值為 0、名為 `AllowStrongNameBypass` 的 DWORD 項目。  
  
-   在 64 位元電腦系統登錄的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 和 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework 機碼下，建立值為 0、名為 `AllowStrongNameBypass` 的 DWORD 項目。  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a>停用單一應用程式的強式名稱略過功能  
  
1.  開啟或建立應用程式組態檔。  
  
     如需此檔案的詳細資訊，請參閱[設定應用程式](../../../docs/framework/configure-apps/index.md)的＜應用程式組態檔＞一節。  
  
2.  新增下列項目：  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 移除組態檔的設定或將屬性設成 "true"，即可還原應用程式的略過功能。  
  
> [!NOTE]
>  只有啟用電腦的略過功能，您才可以開啟或關閉應用程式的強式名稱驗證。 如已關閉電腦的略過功能，即會驗證所有應用程式的強式名稱，而您無法略過單一應用程式的驗證。  
  
## <a name="see-also"></a>另請參閱  
 [Sn.exe (強式名稱工具)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [\<bypassTrustedAppStrongNames> 項目](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)   
 [建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)

