---
title: 中繼資料存放區可程式性
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 4ea6117686b985a9ea18ce4e5cc4ea2b5c25524c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731244"
---
# <a name="metadata-store-programmability"></a><span data-ttu-id="0de52-102">中繼資料存放區可程式性</span><span class="sxs-lookup"><span data-stu-id="0de52-102">Metadata Store Programmability</span></span>
<span data-ttu-id="0de52-103">中繼資料存放區是讓任意中繼資料 (CLR 屬性形式) 與執行階段類型產生關聯的 [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="0de52-103">The metadata store is a [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] feature that allows for the association of arbitrary metadata, in the form of CLR attributes, to types at runtime.</span></span> <span data-ttu-id="0de52-104">這啟用執行階段元件與其設計階段對應項目之間的鬆散結合，也提供變更設計階段元件但不影響執行階段的能力。</span><span class="sxs-lookup"><span data-stu-id="0de52-104">This allows for a loose coupling between the run-time components and their design-time counterparts, as well as the ability to change the design-time components without affecting the runtime.</span></span> <span data-ttu-id="0de52-105">此範例示範如何透過將屬性套用至我們沒有控制權的執行階段類型，對中繼資料存放區撰寫程式。</span><span class="sxs-lookup"><span data-stu-id="0de52-105">The sample shows how to program against the metadata store by applying attributes to a run-time type, the source for which we have no control over.</span></span> <span data-ttu-id="0de52-106">一般用語是主控應用程式註冊一組類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0de52-106">The terminology typically used is that a hosting application registers the metadata for a set of types.</span></span>  
  
 <span data-ttu-id="0de52-107">在輸出中，您可能會注意到額外、 非預期的屬性， <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`。</span><span class="sxs-lookup"><span data-stu-id="0de52-107">Within the output, you may notice an additional, unexpected attribute, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span></span> <span data-ttu-id="0de52-108">這是在使用中繼資料 API 時加入的，對範例執行沒有影響。</span><span class="sxs-lookup"><span data-stu-id="0de52-108">This is added when using the Metadata API and has no impact on the running of the sample.</span></span>  
  
 <span data-ttu-id="0de52-109">這個範例會示範下列情況：</span><span class="sxs-lookup"><span data-stu-id="0de52-109">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0de52-110">示範</span><span class="sxs-lookup"><span data-stu-id="0de52-110">Demonstrates</span></span>  
  
-   <span data-ttu-id="0de52-111">使用中繼資料存放區 API 的屬性插入。</span><span class="sxs-lookup"><span data-stu-id="0de52-111">Attribute injection using the metadata store API.</span></span>  
  
-   <span data-ttu-id="0de52-112">使用回呼機制延後中繼資料註冊。</span><span class="sxs-lookup"><span data-stu-id="0de52-112">Using a callback mechanism to defer metadata registration.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0de52-113">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="0de52-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0de52-114">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 ProgrammingMetadataStore.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="0de52-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ProgrammingMetadataStore.sln solution file.</span></span>  
  
2.  <span data-ttu-id="0de52-115">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="0de52-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="0de52-116">若要執行此方案，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="0de52-116">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0de52-117">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0de52-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0de52-118">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="0de52-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0de52-119">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="0de52-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0de52-120">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="0de52-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`