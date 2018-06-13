---
title: 基本 XAML 僅服務
ms.date: 03/30/2017
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
ms.openlocfilehash: aa6b6ec6930ac90fe95b1cdfcd4cb027de8e5902
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517195"
---
# <a name="basic-xaml-only-service"></a>基本 XAML 僅服務
這個範例會示範如何建立僅限 XAML 的服務。 此案例是針對汽車相關問題的診斷服務。 服務會實作為工作流程，要求客戶回答一系列的問題來診斷此問題。 此服務可以診斷兩種問題 (汽車無法啟動或是空調無法運作)。 工作流程會使用設計工具中的「要求/回覆」範本，公開三個簡單的服務作業。 該服務會裝載在 IIS 中，其做法是在 IIS 中建立虛擬目錄，然後將 service1.xamlx 和 Web.config 檔複製到該虛擬目錄，不需編譯程式碼。 依預設這個範例會自動將複製所需的檔案到當您遵循 WCF 和 WF 範例的安裝指示所建立的虛擬目錄：[的 Windows Communication Foundation範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) Visual Studio 2010 中建立。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入專案方案，然後建立專案。  
  
2.  執行在 [方案基底目錄]\Client\bin\debug 中產生的用戶端應用程式。  
  
3.  此應用程式會列印選項及選取選項。 然後應用程式會詢問某些問題，請回答是或否 (使用 Y/N 按鍵)。 當服務完成問題的診斷之後，應用程式會列印診斷。  
  
4.  應用程式會回到選項。 您可以診斷另一個問題或是結束應用程式。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`