---
title: 基本 XAML 僅服務
ms.date: 03/30/2017
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
ms.openlocfilehash: f4f296a97b9c3093874c5ec8e05023e84b0af44a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268795"
---
# <a name="basic-xaml-only-service"></a><span data-ttu-id="9ea9a-102">基本 XAML 僅服務</span><span class="sxs-lookup"><span data-stu-id="9ea9a-102">Basic XAML only Service</span></span>
<span data-ttu-id="9ea9a-103">這個範例會示範如何建立僅限 XAML 的服務。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-103">This sample demonstrates how to create a XAML only service.</span></span> <span data-ttu-id="9ea9a-104">此案例是針對汽車相關問題的診斷服務。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-104">The scenario is a diagnostics service for car-related problems.</span></span> <span data-ttu-id="9ea9a-105">服務會實作為工作流程，要求客戶回答一系列的問題來診斷此問題。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-105">The service is implemented as a workflow that asks the client a series of questions to diagnose the problem.</span></span> <span data-ttu-id="9ea9a-106">此服務可以診斷兩種問題 (汽車無法啟動或是空調無法運作)。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-106">There are two types of issues the service can diagnose (car does not start or air conditioning not working).</span></span> <span data-ttu-id="9ea9a-107">工作流程會使用設計工具中的「要求/回覆」範本，公開三個簡單的服務作業。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-107">The workflow uses Request/Reply template from the designer to expose three simple service operations.</span></span> <span data-ttu-id="9ea9a-108">該服務會裝載在 IIS 中，其做法是在 IIS 中建立虛擬目錄，然後將 service1.xamlx 和 Web.config 檔複製到該虛擬目錄，不需編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-108">The service is hosted in IIS by creating a virtual directory in IIS and copying the service1.xamlx and Web.config files into the virtual directory, no compiled code is required.</span></span> <span data-ttu-id="9ea9a-109">依預設此範例會將自動複製所需的檔案到建立時遵循的 WCF 和 WF 範例的安裝指示的虛擬目錄： [Windows Communication Foundation範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) Visual Studio 2010 中建置時。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-109">By default this sample will automatically copy the needed files into the virtual directory created when you follow the setup instructions for the WCF and WF samples: [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) when built in Visual Studio 2010.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="9ea9a-110">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="9ea9a-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="9ea9a-111">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入專案方案，然後建立專案。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="9ea9a-112">執行在 [方案基底目錄]\Client\bin\debug 中產生的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-112">Run the Client application generated in [solution base directory]\Client\bin\debug.</span></span>  
  
3.  <span data-ttu-id="9ea9a-113">此應用程式會列印選項及選取選項。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-113">The application prints out options, selects an option.</span></span> <span data-ttu-id="9ea9a-114">然後應用程式會詢問某些問題，請回答是或否 (使用 Y/N 按鍵)。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-114">The application then asks some questions, answer them yes or no (using Y/N keys).</span></span> <span data-ttu-id="9ea9a-115">當服務完成問題的診斷之後，應用程式會列印診斷。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-115">When the service is done diagnosing the issues, the application prints out a diagnosis.</span></span>  
  
4.  <span data-ttu-id="9ea9a-116">應用程式會回到選項。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-116">The application goes back to the options.</span></span> <span data-ttu-id="9ea9a-117">您可以診斷另一個問題或是結束應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-117">You can diagnose another problem or exit the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9ea9a-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9ea9a-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9ea9a-120">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ea9a-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="9ea9a-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`