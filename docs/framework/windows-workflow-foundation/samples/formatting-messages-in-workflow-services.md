---
title: 工作流程服務中的格式化訊息
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eb9a6b3a83a28154dc968bd4c1c41d34028bdd41
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45590191"
---
# <a name="formatting-messages-in-workflow-services"></a>工作流程服務中的格式化訊息
這個範例示範不同使用者類型在訊息活動中的使用方式 (WF 服務)。 範例服務是簡單的經費支出核准服務，會公開三個作業。 `ApproveExpense` 採用資料合約型別，並示範如何使用已知的型別。 作業會根據支出金額傳回 `true` 或 `false`。 `ApprovePO` 接受 XmlSerializer 類型，並傳回`true`或`false`費用金額為基礎。`ApprovedVendor` 接受訊息合約類型，並傳回`true`或`false`如果廠商在核准廠商清單中，或要求來自財務部門 （財務部門可以使用任何廠商）。  
  
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
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`