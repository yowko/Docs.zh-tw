---
title: 緩衝的接收
ms.date: 03/30/2017
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
ms.openlocfilehash: ee53edafc94fd5efd4e412b1b9198a8763b79462
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518707"
---
# <a name="buffered-receive"></a>緩衝的接收
這個範例示範如何安裝及設定緩衝的接收功能在 Windows Workflow Foundation (WF)。 緩衝接收可讓工作流程作者建立工作流程時不必擔心接收訊息的順序。 緩衝接收功能會在本機緩衝處理訊息，並在工作流程準備要接收訊息時傳遞訊息。  
  
## <a name="demonstrates"></a>示範  
 使用緩衝接收搭配訊息活動的失序訊息處理。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a>討論  
 在此範例中，Windows Communication Foundation (WCF) 服務會實作使用[!INCLUDE[wf1](../../../../includes/wf1-md.md)]且一連串<xref:System.ServiceModel.Activities.Receive>活動。 這個工作流程是以簡單貸款核准程序為模型，其中工作流程預期接收三個通知，才會核准貸款。 Windows Communication Foundation (WCF) 用戶端應用程式以服務預期的相反順序傳送三個相互關聯的通知。 因為在服務開啟緩衝接收功能，所以每個失序訊息會在服務緩衝處理，並在工作流程準備要接收訊息時加以處理。  
  
 緩衝接收功能需要繫結的 <xref:System.ServiceModel.Activities.ReceiveContent> 支援，因此服務使用 <xref:System.ServiceModel.NetMsmqBinding>。 不需要繫結的特殊組態檔，因此會使用預設值。  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 服務也會使用 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 來公開服務的中繼資料。  
  
 同樣地，用戶端端點也是使用 <xref:System.ServiceModel.NetMsmqBinding> 設定的。 用戶端程式碼和組態使用所產生**加入服務參考**Visual Studio 功能。 下列範例是在 App.config 檔案中產生的用戶端端點。  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 本範例需要啟用下列 Windows 元件：  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)] 管理相容性、Metabase 和設定相容性  
  
3.  全球資訊網服務、應用程式開發功能和 ASP.NET  
  
4.  Microsoft Message Queues (MSMQ) 伺服器  
  
#### <a name="to-set-up-and-build-the-sample"></a>若要設定和建置範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元中，輸入 `aspnet_regiis –I` 並按 ENTER，註冊 ASP.NET。  
  
2.  以系統管理員身分執行 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。  
  
3.  開啟 LoanService.sln。  
  
4.  當系統詢問您想要建立 LoanService 專案的虛擬目錄，是否選取**是**。  
  
#### <a name="to-set-up-the-service-queues"></a>若要設定服務佇列  
  
1.  按 F5 執行 LoanClient 應用程式，該應用程式會建立佇列以及啟動 Service1.xamlx 中定義的服務。  
  
2.  開啟**電腦管理**從命令提示字元執行 Compmgmt.msc 主控台。  
  
3.  在**電腦管理**主控台中，展開**服務**，**應用程式**，**訊息佇列**，**私用佇列**.  
  
4.  以滑鼠右鍵按一下 loanservice/service1.xamlx 佇列，並選取**屬性**。  
  
5.  選取**安全性**索引標籤，並加入**Everyone 接收訊息**，**查看訊息**和**傳送訊息**權限。  
  
6.  開啟 [[!INCLUDE[iis60](../../../../includes/iis60-md.md)] 管理員]。  
  
7.  瀏覽至**伺服器**，**網站**， **Default Web site**，**私人**， **LoanService**選取**進階的選項**  
  
8.  變更**啟用的通訊協定**是**http**， **net.msmq**。  
  
#### <a name="to-run-the-sample"></a>若要執行範例  
  
1.  瀏覽至http://localhost/private/loanservice/service1.xamlx以確保服務正在執行。  
  
2.  按 F5 執行 LoanClient 應用程式。 一旦工作流程完成時，out.txt 檔案應該會儲存至 C:\Inbox，這個檔案包含訊息交換結果。  
  
#### <a name="to-clean-up"></a>若要清除  
  
1.  開啟**電腦管理**從命令提示字元執行 Compmgmt.msc 主控台。  
  
2.  展開**服務**和**應用程式**，**訊息佇列**，**私用佇列**。  
  
3.  刪除 loanservice/service1.xamlx 佇列。  
  
4.  移除 C:\Inbox 目錄。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
