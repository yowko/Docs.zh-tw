---
title: 可補償的活動範例
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 3bf1d120cd700830a98f53495f7e9989ffec73db
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46477882"
---
# <a name="compensable-activity-sample"></a>可補償的活動範例
這個範例示範如何使用 `CompensableActivity` 活動，定義一般執行期間針對給定動作所執行的工作，以及稍後如有需要，為了補償該動作所必須執行的工作。  此範例的第一個部分說明如何可補償工作單位可以定義在 Windows Workflow Foundation (WF) 使用`CompensableActivity`活動，並在成功執行的執行方式。  範例的第二個部分示範當發生未預期的事件，工作流程執行個體取消時，相同的可補償工作單位如何自動處理補償。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  使用 Visual Studio 2010 開啟 CompensableActivity.sln。  
  
2.  按 CTRL+SHIFT+B 建置此方案。  
  
3.  按 F5 鍵執行應用程式。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`