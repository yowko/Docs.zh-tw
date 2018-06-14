---
title: 使用活動中的 AsyncOperationContext 範例
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: da7b62ef9e29621d1e6ee1046afb5455af1164bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515493"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a>使用活動中的 AsyncOperationContext 範例
這個範例示範如何開發自訂的 <xref:System.Activities.CodeActivity>，該活動會使用 <xref:System.Activities.AsyncCodeActivityContext> 在工作流程之外以非同步方式執行工作。  
  
## <a name="sample-details"></a>範例詳細資料  
 範例活動會使用 <xref:System.IO.FileStream.BeginWrite%2A> 類別上的 <xref:System.IO.FileStream.EndWrite%2A> 和 <xref:System.IO.FileStream> 方法，以非同步方式將資料寫入檔案中。 此處介紹的模式可加以調整，以應用於其他非同步方法。 非同步作業執行時，工作流程中的其他活動也可以執行，不過工作流程無法保存。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 [Async.sln] 範例方案。  
  
2.  建置並執行方案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`