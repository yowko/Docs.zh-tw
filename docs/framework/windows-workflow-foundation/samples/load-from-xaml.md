---
title: 從 XAML 載入
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: d07ddef8fb982aa0bf707cb688cd23f04bb231d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142715"
---
# <a name="load-from-xaml"></a><span data-ttu-id="a8a1a-102">從 XAML 載入</span><span class="sxs-lookup"><span data-stu-id="a8a1a-102">Load From XAML</span></span>
<span data-ttu-id="a8a1a-103">這個範例示範如何動態載入 XAML 工作流程，而不必執行 XamlBuildTask 工具。</span><span class="sxs-lookup"><span data-stu-id="a8a1a-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="a8a1a-104">這個範例會改為呼叫 <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a8a1a-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="a8a1a-105">該示例是一個 Windows 演示文稿基礎 （WPF） 用戶端應用程式，該應用程式使用<xref:System.Activities.XamlIntegration.ActivityXamlServices>類載入 XAML 工作流並執行它們。</span><span class="sxs-lookup"><span data-stu-id="a8a1a-105">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="a8a1a-106">使用 <xref:System.Activities.XamlIntegration.ActivityXamlServices> 類別載入工作流程之後，就會傳回可以執行的 <xref:System.Activities.DynamicActivity%601>。</span><span class="sxs-lookup"><span data-stu-id="a8a1a-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="a8a1a-107">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="a8a1a-107">To use this sample</span></span>

1. <span data-ttu-id="a8a1a-108">使用 Visual Studio 2010，打開 LoadFromXAML.sln 解決方案檔。</span><span class="sxs-lookup"><span data-stu-id="a8a1a-108">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="a8a1a-109">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="a8a1a-109">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="a8a1a-110">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="a8a1a-110">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8a1a-111">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a8a1a-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a8a1a-112">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a8a1a-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a8a1a-113">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="a8a1a-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8a1a-114">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a8a1a-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
