---
title: 工作流程服務中的格式化訊息
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eac9f7042dbcbd31f9a8c7d5e56c7b7d2ab62156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="formatting-messages-in-workflow-services"></a>工作流程服務中的格式化訊息
這個範例示範不同使用者類型在訊息活動中的使用方式 (WF 服務)。 範例服務是簡單的經費支出核准服務，會公開三個作業。 `ApproveExpense` 採用資料合約型別，並示範如何使用已知的型別。 作業會根據支出金額傳回 `true` 或 `false`。 `ApprovePO` 會採用 XmlSerializer 型別並傳回`true`或`false`根據支出金額。`ApprovedVendor` 採用訊息合約型別，並傳回`true`或`false`如果廠商在核准廠商清單中，或者要求來自財務部門 （財務部門可以使用任何廠商）。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入專案方案，然後建立專案。  
  
2.  首先，執行 [方案基底目錄]\FormatterService\bin\debug\ 中產生的服務。  
  
3.  接著，執行 [方案基底目錄]\FormatterClient\bin\debug 中產生的用戶端應用程式。  
  
4.  這個用戶端會在服務上呼叫三個作業並列印結果。 完成時，按下 ENTER 結束用戶端和服務。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`