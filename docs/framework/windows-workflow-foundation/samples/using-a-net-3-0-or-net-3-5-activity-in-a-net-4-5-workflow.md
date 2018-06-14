---
title: 在 .NET Framework 4.5 工作流程中使用 .NET Framework 3.0 或 .NET Framework 3.5 活動
ms.date: 03/30/2017
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
ms.openlocfilehash: ab2e93918617bd1ca21fb32878d446db0dd2ef16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514895"
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a>在 .NET Framework 4.5 工作流程中使用 .NET Framework 3.0 或 .NET Framework 3.5 活動
<xref:System.Activities.Statements.Interop>活動可讓您執行中的.NET Framework 3.0 Windows Workflow Foundation (WF) 活動[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]工作流程。 這個範例示範如何使用 <xref:System.Activities.Statements.Interop> 活動，將字串當做引數傳遞至自訂 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 活動。  
  
## <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 SimpleInterop.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a>另請參閱
