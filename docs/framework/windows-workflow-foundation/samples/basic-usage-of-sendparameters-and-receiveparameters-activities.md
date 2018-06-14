---
title: SendParameters 及 ReceiveParameters 活動的基本使用
ms.date: 03/30/2017
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
ms.openlocfilehash: 8732b10f3f96ccf9ed352f9b54c60a4ee0d1664c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515394"
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a>SendParameters 及 ReceiveParameters 活動的基本使用
這個範例示範 <xref:System.ServiceModel.Activities.SendParametersContent> 和 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 的使用方式。 服務會公開依向作業，該作業會使用字串引數並將輸入 echo 至用戶端。 這個範例將示範如何設定這些訊息處理活動的參數。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a>使用這個範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入專案方案，然後建立專案。  
  
2.  請先執行 [方案基底目錄]\EchoWorkflowService\bin\debug 中產生的 EchoWorkflowService 應用程式。  
  
3.  接著執行 [方案基底目錄]\EchoWorkflowClient\bin\debug 中產生的 EchoWorkflowClient 應用程式。  
  
4.  用戶端會在服務上呼叫 Echo 作業並列印結果。 完成時，按下 ENTER 結束用戶端和服務。