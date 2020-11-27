---
title: 從 XAML 載入
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: ebf6ebe1001773768d8da318a0d6b68d50c7848c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283558"
---
# <a name="load-from-xaml"></a>從 XAML 載入

這個範例示範如何動態載入 XAML 工作流程，而不必執行 XamlBuildTask 工具。 這個範例會改為呼叫 <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> 方法。 此範例是 Windows Presentation Foundation (WPF) 用戶端應用程式，它會使用類別載入 XAML 工作流程 <xref:System.Activities.XamlIntegration.ActivityXamlServices> ，並執行這些工作流程。 使用 <xref:System.Activities.XamlIntegration.ActivityXamlServices> 類別載入工作流程之後，就會傳回可以執行的 <xref:System.Activities.DynamicActivity%601>。

#### <a name="to-use-this-sample"></a>若要使用這個範例

1. 使用 Visual Studio 2010，開啟 LoadFromXAML .sln 方案檔。

2. 若要建置此方案，請按 CTRL+SHIFT+B。

3. 若要執行此方案，請按下 CTRL+F5。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
