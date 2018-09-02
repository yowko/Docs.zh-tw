---
title: Expressions2
ms.date: 03/30/2017
ms.assetid: 43a85905-77b5-4893-bb38-1cb9b293d69d
ms.openlocfilehash: e852b62e6d0b6b4b3ddc19b197902de5325310a1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464865"
---
# <a name="expressions"></a>運算式
這個範例示範如何在工作流程中使用基本運算式。 其中包含的工作流程會計算某虛構公司兩個員工的基本薪資統計資料。 兩個類別 `Employee` 和 `SalaryStats` 定義於 Employee.cs 和 SalaryStats.cs。 工作流程中使用這些類別，示範如何對複雜類型的變數屬性執行簡單算術和字串運算。  
  
 薪資計算工作流程同時以 XAML 和 C# 定義，示範兩種撰寫樣式。 XAML 版本是包含於 SalaryCalculation.xaml，可在工作流程設計工具中檢視和編輯。 C# 版本是位於 Program.cs。 XAML 中使用的運算式符合 Visual Basic 語法，會使用 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 和 <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> 運算式活動來執行。 如需有關 Visual Basic 運算式，請參閱 < [Visual Basic 運算式](https://go.microsoft.com/fwlink/?LinkId=165912)。 另一方面，C# 運算式是撰寫為 Lambda 運算式，會使用 <xref:System.Activities.Expressions.LambdaValue%601> 和 <xref:System.Activities.Expressions.LambdaReference%601> 運算式活動。 將運算式撰寫為 Lambda 運算式允許 C# 編譯器提供語法反白顯示和靜態驗證。 如需有關 C# 中 lambda 運算式的詳細資訊，請參閱 < [Lambda 運算式 （C# 程式設計手冊）](https://go.microsoft.com/fwlink/?LinkId=182082)。 如果在程式碼中使用 Visual Basic 來撰寫工作流程，則會使用 Visual Basic Lambda 運算式。 如需有關在 Visual Basic 中的 lambda 運算式的詳細資訊，請參閱 < [Lambda 運算式 (Visual Basic)](https://go.microsoft.com/fwlink/?LinkId=152437)。 如需使用程式碼撰寫工作流程的相關詳細資訊，請參閱 <<c0> [ 撰寫工作流程、 活動和運算式使用命令式程式碼](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)。  
  
#### <a name="to-run-the-sample"></a>若要執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 Expressions.sln 方案。  
  
2.  按下 CTRL + SHIFT + B 建置方案，或選取**建置方案**從**建置**功能表。  
  
    > [!NOTE]
    >  若要在 Visual Studio 設計工具中開啟 SalaryCalculation.xaml，您必須先編譯專案，確認 `Employee` 和 `SalaryStats` 類別可用於設計工具。  
  
3.  成功組建後，按 F5 或選取**開始偵錯**從**偵錯**功能表。 或者您可以按 Ctrl + F5 或選取**啟動但不偵錯**從**偵錯**執行，而不偵錯 功能表。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Expressions`