---
title: LINQ 訊息查詢相互關聯
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 202d65914d32245952f308d3115ec93231f95f15
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989331"
---
# <a name="linq-message-query-correlation"></a>LINQ 訊息查詢相互關聯
這個範例示範如何使用自訂 <xref:System.ServiceModel.Dispatcher.MessageQuery> 實作 (而不是系統提供的 <xref:System.ServiceModel.XPathMessageQuery>) 來執行以內容為主的相互關聯。  
  
## <a name="demonstrates"></a>示範  
 自訂 <xref:System.ServiceModel.Dispatcher.MessageQuery>、以內容為主的相互關聯。  
  
## <a name="discussion"></a>討論  
 這個範例示範如何為了相互關聯，從 <xref:System.ServiceModel.Dispatcher.MessageQuery> 基底類別延伸。 `LinqMessageQuery` 自訂實作可讓使用者提供 XName，以使用 XLinq 在訊息中尋找。 查詢所擷取的資料是用來形成相互關聯索引鍵，以便將訊息分派至適當的工作流程執行個體。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 這個範例使用 HTTP 端點公開工作流程服務。 若要執行此範例，必須新增適當的 URL Acl （如需詳細資訊，請參閱設定[HTTP 和 HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) ），方法是以系統管理員身分執行 Visual Studio，或在已提升許可權的提示字元中執行下列命令，以新增適當的 acl。 請確定您的網域和使用者名稱已用來取代。  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. 一旦加入 URL ACL，請使用下列步驟。  
  
    1. 建置方案。  
  
    2. 以滑鼠右鍵按一下方案，然後選取 [**設定啟始專案**]，以設定多個啟動專案。 將**服務**和**用戶端**（依該順序）新增為多個啟動專案。  
  
    3. 執行應用程式。 用戶端主控台會顯示傳送訂單及接收採購單識別碼、後續確認訂單的工作流程。 服務視窗會顯示正在處理的要求。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
