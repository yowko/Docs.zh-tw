---
title: LINQ 訊息查詢相互關聯
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 507001b165efdcbe7c1e27a07749dbe2eafb468f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182811"
---
# <a name="linq-message-query-correlation"></a>LINQ 訊息查詢相互關聯
這個範例示範如何使用自訂 <xref:System.ServiceModel.Dispatcher.MessageQuery> 實作 (而不是系統提供的 <xref:System.ServiceModel.XPathMessageQuery>) 來執行以內容為主的相互關聯。  
  
## <a name="demonstrates"></a>示範  
 自訂 <xref:System.ServiceModel.Dispatcher.MessageQuery>、以內容為主的相互關聯。  
  
## <a name="discussion"></a>討論區  
 這個範例示範如何為了相互關聯，從 <xref:System.ServiceModel.Dispatcher.MessageQuery> 基底類別延伸。 `LinqMessageQuery` 自訂實作可讓使用者提供 XName，以使用 XLinq 在訊息中尋找。 查詢所擷取的資料是用來形成相互關聯索引鍵，以便將訊息分派至適當的工作流程執行個體。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 這個範例使用 HTTP 端點公開工作流程服務。 要運行此示例，必須添加正確的 URL ACL（請參閱[配置 HTTP 和 HTTPS](../../wcf/feature-details/configuring-http-and-https.md)瞭解詳細資訊），方法是以管理員身份運行 Visual Studio，或者通過提升的提示執行以下命令以添加相應的 ACL。 請確定您的網域和使用者名稱已用來取代。  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. 一旦加入 URL ACL，請使用下列步驟。  
  
    1. 建置方案。  
  
    2. 通過按右鍵解決方案並選擇 **"設置啟動專案"** 來設置多個啟動專案。 將**服務和****用戶端**（按該順序）添加為多個啟動專案。  
  
    3. 執行應用程式。 用戶端主控台會顯示傳送訂單及接收採購單識別碼、後續確認訂單的工作流程。 服務視窗會顯示正在處理的要求。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
