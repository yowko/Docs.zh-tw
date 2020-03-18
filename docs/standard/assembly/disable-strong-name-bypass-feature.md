---
title: 如何：禁用強式名稱旁路功能
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: a4c4ae7ea61a659d3bede532da3c1bdaea448873
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141114"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>如何：禁用強式名稱旁路功能
從 .NET Framework 3.5 版 Service Pack 1 (SP1) 開始，當組件載入到完全信任的 <xref:System.AppDomain> 物件 (例如適用於 `MyComputer` 區域的預設 <xref:System.AppDomain>) 時，不會驗證強式名稱簽章。 這是指強式名稱略過功能。 在完全信任環境中，不論簽章為何，已簽署、完全信任的組件要求 <xref:System.Security.Permissions.StrongNameIdentityPermission> 一律會成功。 唯一的限制是組件必須是完全受信任的，因為它的區域是完全信任的。 因為強式名稱不是這些情況下的決定因素，所以不需要進行驗證。 略過強式名稱簽章驗證可大幅提升效能。  
  
 略過功能適用於任何完全信任的組件，該組件非延遲簽署，且已從其 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性指定的目錄載入至所有完全信任的 <xref:System.AppDomain>。  
  
 您可以設定登錄機碼值，覆寫電腦上所有應用程式的略過功能。 您可以使用應用程式組態檔覆寫單一應用程式的設定。 如果登錄機碼已停用該功能，您即無法恢復單一應用程式的略過功能。  
  
 當您覆寫略過功能時，只會驗證強式名稱的正確性，不檢查 <xref:System.Security.Permissions.StrongNameIdentityPermission>。 如果您想要確認特定的強式名稱，您必須另外執行檢查。  
  
> [!IMPORTANT]
> 能否強制執行強式名稱驗證，視登錄機碼而定，如下列程序所述。 如果在沒有存取控制清單 (ACL) 權限的帳戶下，執行應用程式存取該登錄機碼，則設定為無效。 您必須確定此機碼已設定 ACL 權限，它才能為所有組件讀取。  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a>禁用所有應用程式的強式名稱旁路功能  
  
- 在 32 位元電腦系統登錄的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 機碼下，建立值為 0、名為 `AllowStrongNameBypass` 的 DWORD 項目。  
  
- 在 64 位元電腦系統登錄的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 和 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework 機碼下，建立值為 0、名為 `AllowStrongNameBypass` 的 DWORD 項目。  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a>禁用單個應用程式的強式名稱旁路功能  
  
1. 開啟或建立應用程式組態檔。  
  
    有關此檔的詳細資訊，請參閱["配置應用程式](../../framework/configure-apps/index.md)"中的應用程式佈建檔部分。  
  
2. 新增下列項目：  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 您可以通過刪除設定檔設置或將屬性設置為`true`還原應用程式的旁路功能。  
  
> [!NOTE]
> 只有啟用電腦的略過功能，您才可以開啟或關閉應用程式的強式名稱驗證。 如已關閉電腦的略過功能，即會驗證所有應用程式的強式名稱，而您無法略過單一應用程式的驗證。  
  
## <a name="see-also"></a>另請參閱

- [Sn.exe (強式名稱工具)](../../framework/tools/sn-exe-strong-name-tool.md)
- [\<繞過受信任的AppStrongnames>元素](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [建立和使用強式名稱的組件](create-use-strong-named.md)
