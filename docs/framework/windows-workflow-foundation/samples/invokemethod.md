---
title: InvokeMethod
ms.date: 03/30/2017
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
ms.openlocfilehash: 861e0cf160aec9814abcf8c27c37ce13a5d88b2a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43457177"
---
# <a name="invokemethod"></a>InvokeMethod
這個範例示範以不同的方式使用 <xref:System.Activities.Statements.InvokeMethod> 活動叫用類別的方法。  
  
 方法屬於類別，且代表包含的作業集。 <xref:System.Activities.Statements.InvokeMethod> 活動讓您能夠針對物件或型別呼叫方法、傳遞參數，以及取得傳回值。 方法可以採同步或非同步的方式叫用。  
  
## <a name="sample-details"></a>範例詳細資料  
 這個範例使用 <xref:System.Activities.Statements.InvokeMethod> 活動執行下列案例：  
  
1.  叫用不含參數的執行個體方法。  
  
2.  使用兩個參數 (<xref:System.String> 和 <xref:System.Int32>) 叫用執行個體方法。  
  
3.  使用兩個參數 (<xref:System.String> 和 <xref:System.Int32>) 和 <xref:System.String>[] 型別的參數陣列叫用執行個體方法。  
  
4.  使用型別 <xref:System.Int32> 的兩個參數和型別 <xref:System.Int32> 的結果叫用執行個體方法。 在這個案例中，結果值會繫結至變數並且在另一個活動中使用。 該值會使用 <xref:System.Activities.Statements.WriteLine> 活動在主控台中顯示。  
  
5.  使用 <xref:System.String> 和 <xref:System.Int32> 型別的兩個參數叫用靜態方法。  
  
6.  使用型別 <xref:System.String> 的一個泛型參數叫用執行個體方法。  
  
7.  使用 <xref:System.String> 和 <xref:System.Int32> 型別的兩個泛型參數叫用靜態方法。  
  
8.  叫用執行個體方法，該方法的其中一個參數是由型別 <xref:System.String> 的參考所傳遞。 在這個案例中，參考參數會繫結至變數 (`outParam`) 並且在另一個活動中使用。 它會使用 <xref:System.Activities.Statements.WriteLine> 活動在主控台上顯示。  
  
9. 叫用非同步執行個體方法。  
  
10. 使用兩個 <xref:System.Activities.Statements.InvokeMethod> 活動在物件的同一個執行個體上叫用兩個不同的方法。  
  
11. 在物件的執行個體中儲存值。  
  
12. 從物件的執行個體擷取值。  
  
## <a name="to-use-this-sample"></a>若要使用這個範例  
 這個範例會以兩種版本提供。 此範例的第一個版本示範如何使用<xref:System.Activities.Statements.InvokeMethod>透過 C# 程式碼使用 Windows Workflow Foundation (WF) 的程式設計模型，並可以在 CodedWorkflow\CS 資料夾中找到。 這個範例的第二個版本示範使用 XAML 的 <xref:System.Activities.Statements.InvokeMethod> 使用方式，這個版本可以在 DesignerWorkflow\CS 資料夾中找到。  
  
#### <a name="to-run-the-coded-workflow-sample"></a>若要執行編碼的工作流程範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 CodedWorkflow\CS 資料夾中的 [InvokeMethodUsage.sln] 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
#### <a name="to-run-the-designer-workflow-sample"></a>若要執行設計工具工作流程範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 DesignerWorkflow\CS 資料夾中的 [InvokeMethodUsage.sln] 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`