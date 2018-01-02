---
title: "增益集和擴充性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
caps.latest.revision: "42"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e4d336992be216178b1237c9f43bffb3de61fba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="add-ins-and-extensibility"></a><span data-ttu-id="c40a6-102">增益集和擴充性</span><span class="sxs-lookup"><span data-stu-id="c40a6-102">Add-ins and Extensibility</span></span>
<a name="top"></a> <span data-ttu-id="c40a6-103">增益集可以為主應用程式提供擴充的功能或服務。</span><span class="sxs-lookup"><span data-stu-id="c40a6-103">Add-ins provide extended features or services for a host application.</span></span> <span data-ttu-id="c40a6-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供程式設計模型，開發人員可用來開發增益集，並且在其主應用程式中加以啟動。</span><span class="sxs-lookup"><span data-stu-id="c40a6-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a programming model that developers can use to develop add-ins and activate them in their host application.</span></span> <span data-ttu-id="c40a6-105">模型的做法是在主應用程式與增益集之間建構通訊管線。</span><span class="sxs-lookup"><span data-stu-id="c40a6-105">The model achieves this by constructing a communication pipeline between the host and the add-in.</span></span> <span data-ttu-id="c40a6-106">此模型是藉由使用 <xref:System.AddIn>、 <xref:System.AddIn.Hosting>、 <xref:System.AddIn.Pipeline>和 <xref:System.AddIn.Contract> 命名空間中的類型來實作。</span><span class="sxs-lookup"><span data-stu-id="c40a6-106">The model is implemented by using the types in the <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, and <xref:System.AddIn.Contract> namespaces.</span></span>  
  
 <span data-ttu-id="c40a6-107">本概觀包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="c40a6-107">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="c40a6-108">增益集模型</span><span class="sxs-lookup"><span data-stu-id="c40a6-108">Add-in Model</span></span>](#addin_model)  
  
-   [<span data-ttu-id="c40a6-109">增益集與主應用程式的區別</span><span class="sxs-lookup"><span data-stu-id="c40a6-109">Distinguishing Between Add-ins and Hosts</span></span>](#distinguishing_between_addins_and_hosts)  
  
-   [<span data-ttu-id="c40a6-110">相關主題</span><span class="sxs-lookup"><span data-stu-id="c40a6-110">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="c40a6-111">參考資料</span><span class="sxs-lookup"><span data-stu-id="c40a6-111">Reference</span></span>](#reference)  
  
> [!NOTE]
>  <span data-ttu-id="c40a6-112">您可以在 [CodePlex 的 Managed 擴充性和增益集架構網站](http://go.microsoft.com/fwlink/?LinkId=121190)上找到其他範例程式碼，以及用來建立增益集管線之工具的客戶技術預覽。</span><span class="sxs-lookup"><span data-stu-id="c40a6-112">You can find additional sample code, and customer technology previews of tools for building add-in pipelines, at the [Managed Extensibility and Add-In Framework site on CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).</span></span>  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a><span data-ttu-id="c40a6-113">增益集模型</span><span class="sxs-lookup"><span data-stu-id="c40a6-113">Add-in Model</span></span>  
 <span data-ttu-id="c40a6-114">增益集模型是由一連串區段所組成，這些區段構成增益集管線 (也稱為通訊管線)，負責增益集與主應用程式之間的所有通訊。</span><span class="sxs-lookup"><span data-stu-id="c40a6-114">The add-in model consists of a series of segments that make up the add-in pipeline (also known as the communication pipeline), that is responsible for all communication between the add-in and the host.</span></span> <span data-ttu-id="c40a6-115">管線是區段的對稱式通訊模型，這些區段會在增益集及其主應用程式之間交換資料。</span><span class="sxs-lookup"><span data-stu-id="c40a6-115">The pipeline is a symmetrical communication model of segments that exchange data between an add-in and its host.</span></span> <span data-ttu-id="c40a6-116">在主應用程式與增益集之間開發這些區段，可提供必要的抽象層，以支援增益集的版本控制和隔離。</span><span class="sxs-lookup"><span data-stu-id="c40a6-116">Developing these segments between the host and the add-in provides the required layers of abstraction that support versioning and isolation of the add-in.</span></span>  
  
 <span data-ttu-id="c40a6-117">下圖顯示管線。</span><span class="sxs-lookup"><span data-stu-id="c40a6-117">The following illustration shows the pipeline.</span></span>  
  
 <span data-ttu-id="c40a6-118">![新增 &#45; 管線模型中。] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span><span class="sxs-lookup"><span data-stu-id="c40a6-118">![Add&#45;in pipeline model.](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span></span>  
<span data-ttu-id="c40a6-119">增益集管線</span><span class="sxs-lookup"><span data-stu-id="c40a6-119">Add-in pipeline</span></span>  
  
 <span data-ttu-id="c40a6-120">這些區段的組件不一定要在相同的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="c40a6-120">The assemblies for these segments are not required to be in the same application domain.</span></span> <span data-ttu-id="c40a6-121">您可以將增益集載入至其本身的新應用程式定義域、現有的應用程式定義域，甚至主機的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="c40a6-121">You can load an add-in into its own new application domain, into an existing application domain, or even into the host's application domain.</span></span> <span data-ttu-id="c40a6-122">您可以將多個增益集載入相同的應用程式定義域中，讓增益集能夠共用資源和安全性內容。</span><span class="sxs-lookup"><span data-stu-id="c40a6-122">You can load multiple add-ins into the same application domain, which enables the add-ins to share resources and security contexts.</span></span>  
  
 <span data-ttu-id="c40a6-123">增益集模型可支援並建議主應用程式與增益集之間的選擇性界限，就是所謂的隔離界限 (又稱為遠端界限)。</span><span class="sxs-lookup"><span data-stu-id="c40a6-123">The add-in model supports, and recommends, an optional boundary between the host and the add-in, which is called the isolation boundary (also known as a remoting boundary).</span></span> <span data-ttu-id="c40a6-124">這個界限可以是應用程式定義域或處理序界限。</span><span class="sxs-lookup"><span data-stu-id="c40a6-124">This boundary can be an application domain or process boundary.</span></span>  
  
 <span data-ttu-id="c40a6-125">管線中間的合約區段會載入至主應用程式定義域和增益集的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="c40a6-125">The contract segment in the middle of the pipeline is loaded into both the host's application domain and the add-in's application domain.</span></span> <span data-ttu-id="c40a6-126">此合約會定義主應用程式和增益集用來彼此交換類型的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="c40a6-126">The contract defines the virtual methods that the host and the add-in use to exchange types with each other.</span></span>  
  
 <span data-ttu-id="c40a6-127">若要通過隔離界限，類型必須是合約或可序列化的類型。</span><span class="sxs-lookup"><span data-stu-id="c40a6-127">To pass through the isolation boundary, types must be either contracts or serializable types.</span></span> <span data-ttu-id="c40a6-128">不是合約或可序列化的類型，必須由管線中的配接器區段轉換成合約。</span><span class="sxs-lookup"><span data-stu-id="c40a6-128">Types that are not contracts or serializable types must be converted to contracts by the adapter segments in the pipeline.</span></span>  
  
 <span data-ttu-id="c40a6-129">管線的檢視區段是抽象基底類別或介面，依照合約的定義，提供主應用程式和增益集其共用方法的檢視。</span><span class="sxs-lookup"><span data-stu-id="c40a6-129">The view segments of the pipeline are abstract base classes or interfaces that provide the host and the add-in with a view of the methods that they share, as defined by the contract.</span></span>  
  
 <span data-ttu-id="c40a6-130">如需有關開發管線區段的詳細資訊，請參閱 [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md)。</span><span class="sxs-lookup"><span data-stu-id="c40a6-130">For more information about developing pipeline segments, see [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md).</span></span>  
  
 <span data-ttu-id="c40a6-131">以下各節說明增益集模型的功能。</span><span class="sxs-lookup"><span data-stu-id="c40a6-131">The sections that follow describe the features of the add-in model.</span></span>  
  
### <a name="independent-versioning"></a><span data-ttu-id="c40a6-132">獨立版本設定</span><span class="sxs-lookup"><span data-stu-id="c40a6-132">Independent Versioning</span></span>  
 <span data-ttu-id="c40a6-133">此增益集模型可讓主應用程式和增益集獨立進行版本設定。</span><span class="sxs-lookup"><span data-stu-id="c40a6-133">The add-in model allows hosts and add-ins to version independently.</span></span> <span data-ttu-id="c40a6-134">所以此增益集模型可用於下列案例：</span><span class="sxs-lookup"><span data-stu-id="c40a6-134">As a result, the add-in model enables the following scenarios:</span></span>  
  
-   <span data-ttu-id="c40a6-135">建立配接器，讓主應用程式能夠使用針對舊版主應用程式建置的增益集。</span><span class="sxs-lookup"><span data-stu-id="c40a6-135">Creating an adapter that enables a host to use an add-in built for a previous version of the host.</span></span>  
  
-   <span data-ttu-id="c40a6-136">建立配接器，讓主應用程式能夠使用針對新版主應用程式建置的增益集。</span><span class="sxs-lookup"><span data-stu-id="c40a6-136">Creating an adapter that enables a host to use an add-in built for a later version of the host.</span></span>  
  
-   <span data-ttu-id="c40a6-137">建立配接器，讓主應用程式能夠使用針對不同主應用程式建置的增益集。</span><span class="sxs-lookup"><span data-stu-id="c40a6-137">Creating an adapter that enables a host to use add-ins built for a different host.</span></span>  
  
### <a name="discovery-and-activation"></a><span data-ttu-id="c40a6-138">探索和啟動</span><span class="sxs-lookup"><span data-stu-id="c40a6-138">Discovery and Activation</span></span>  
 <span data-ttu-id="c40a6-139">若要啟動增益集，您可以使用從資訊存放區找到之增益集集合中的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c40a6-139">You can activate an add-in by using a token from a collection that represents the add-ins found from an information store.</span></span> <span data-ttu-id="c40a6-140">若要尋找增益集，您可以搜尋用來定義增益集之主應用程式檢視的類型。</span><span class="sxs-lookup"><span data-stu-id="c40a6-140">Add-ins are found by searching for the type that defines the host's view of the add-in.</span></span> <span data-ttu-id="c40a6-141">您也可以依據定義增益集的類型來尋找特定增益集。</span><span class="sxs-lookup"><span data-stu-id="c40a6-141">You can also find a specific add-in by the type that defines the add-in.</span></span> <span data-ttu-id="c40a6-142">資訊存放區是由兩個快取檔案所組成：管線存放區和增益集存放區。</span><span class="sxs-lookup"><span data-stu-id="c40a6-142">The information store consists of two cache files: the pipeline store and the add-in store.</span></span>  
  
 <span data-ttu-id="c40a6-143">如需更新和重建資訊存放區的相關資訊，請參閱 [增益集探索](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421)。</span><span class="sxs-lookup"><span data-stu-id="c40a6-143">For information about updating and rebuilding the information store, see [Add-in Discovery](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421).</span></span> <span data-ttu-id="c40a6-144">如需啟動增益集的相關資訊，請參閱 [增益集啟動](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) 和 [如何：以不同的隔離和安全性啟動增益集](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5)。</span><span class="sxs-lookup"><span data-stu-id="c40a6-144">For information about activating add-ins, see [Add-in Activation](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) and [How to: Activate Add-ins with Different Isolation and Security](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="isolation-levels-and-external-processes"></a><span data-ttu-id="c40a6-145">隔離等級和外部處理序</span><span class="sxs-lookup"><span data-stu-id="c40a6-145">Isolation Levels and External Processes</span></span>  
 <span data-ttu-id="c40a6-146">此增益集模型可支援增益集及其主應用程式之間或增益集之間的數個隔離等級。從最低的隔離等級開始，這些等級如下：</span><span class="sxs-lookup"><span data-stu-id="c40a6-146">The add-in model supports several levels of isolation between an add-in and its host or between add-ins. Starting from the least isolated, these levels are as follows:</span></span>  
  
-   <span data-ttu-id="c40a6-147">增益集在與主應用程式相同的應用程式定義域中執行。</span><span class="sxs-lookup"><span data-stu-id="c40a6-147">The add-in runs in the same application domain as the host.</span></span> <span data-ttu-id="c40a6-148">不建議這麼做，因為這樣就少了使用不同應用程式定義域時所提供的隔離和卸載功能。</span><span class="sxs-lookup"><span data-stu-id="c40a6-148">This is not recommended because you lose the isolation and unloading capabilities that you get when you use different application domains.</span></span>  
  
-   <span data-ttu-id="c40a6-149">多個增益集載入至相同的應用程式定義域中，而其不同於主應用程式所使用的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="c40a6-149">Multiple add-ins are loaded into the same application domain that is different from the application domain used by the host.</span></span>  
  
-   <span data-ttu-id="c40a6-150">每個增益集都獨自載入至其本身的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="c40a6-150">Each add-in is loaded exclusively into its own application domain.</span></span> <span data-ttu-id="c40a6-151">這是最常見的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="c40a6-151">This is the most common level of isolation.</span></span>  
  
-   <span data-ttu-id="c40a6-152">多個增益集在外部處理序中，載入至相同的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="c40a6-152">Multiple add-ins are loaded into the same application domain in an external process.</span></span>  
  
-   <span data-ttu-id="c40a6-153">每個增益集都在外部處理序中，獨自載入至其本身的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="c40a6-153">Each add-in is loaded exclusively into its own application domain in an external process.</span></span> <span data-ttu-id="c40a6-154">這是隔離等級最高的案例。</span><span class="sxs-lookup"><span data-stu-id="c40a6-154">This is the most isolated scenario.</span></span>  
  
 <span data-ttu-id="c40a6-155">如需有關使用外部處理序的詳細資訊，請參閱 [如何：以不同的隔離和安全性來啟動增益集](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5)。</span><span class="sxs-lookup"><span data-stu-id="c40a6-155">For more information about using external processes, see [How to: Activate Add-ins with Different Isolation and Security](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="lifetime-management"></a><span data-ttu-id="c40a6-156">存留期管理</span><span class="sxs-lookup"><span data-stu-id="c40a6-156">Lifetime Management</span></span>  
 <span data-ttu-id="c40a6-157">由於增益集模型跨越應用程式定義域和處理序界限，因此記憶體回收本身並不足以釋放及回收物件。</span><span class="sxs-lookup"><span data-stu-id="c40a6-157">Because the add-in model spans application domain and process boundaries, garbage collection by itself is not sufficient to release and reclaim objects.</span></span> <span data-ttu-id="c40a6-158">增益集模型提供一種生命週期管理機制，其使用語彙基元和參考計數，而且通常不需要額外的程式設計。</span><span class="sxs-lookup"><span data-stu-id="c40a6-158">The add-in model provides a lifetime management mechanism that uses tokens and reference counting, and usually does not require additional programming.</span></span> <span data-ttu-id="c40a6-159">如需詳細資訊，請參閱 [生命週期管理](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5)。</span><span class="sxs-lookup"><span data-stu-id="c40a6-159">For more information, see [Lifetime Management](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
 [<span data-ttu-id="c40a6-160">回到頁首</span><span class="sxs-lookup"><span data-stu-id="c40a6-160">Back to top</span></span>](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a><span data-ttu-id="c40a6-161">增益集與主應用程式的區別</span><span class="sxs-lookup"><span data-stu-id="c40a6-161">Distinguishing Between Add-ins and Hosts</span></span>  
 <span data-ttu-id="c40a6-162">增益集與主應用程式之間的差異，只在於增益集是由主應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="c40a6-162">The difference between an add-in and a host is merely that the host is the one that activates the add-in.</span></span> <span data-ttu-id="c40a6-163">主應用程式可以是兩者中較大的一個，例如文字處理應用程式及其拼字檢查工具；或者，主應用程式可以是兩者中較小的一個，例如內嵌媒體播放程式的立即訊息用戶端。</span><span class="sxs-lookup"><span data-stu-id="c40a6-163">The host can be the larger of the two, such as a word processing application and its spell checkers; or the host can be the smaller of the two, such as an instant messaging client that embeds a media player.</span></span> <span data-ttu-id="c40a6-164">此增益集模型支援用戶端及伺服器案例中的增益集。</span><span class="sxs-lookup"><span data-stu-id="c40a6-164">The add-in model supports add-ins in both client and server scenarios.</span></span> <span data-ttu-id="c40a6-165">伺服器增益集的範例，包括為郵件伺服器提供病毒掃描、垃圾郵件篩選和 IP 保護的增益集。</span><span class="sxs-lookup"><span data-stu-id="c40a6-165">Examples of server add-ins include add-ins that provide mail servers with virus scanning, spam filters, and IP protection.</span></span> <span data-ttu-id="c40a6-166">用戶端增益集的範例，包括文書處理器的參考增益集、圖形程式和遊戲的特製化功能，以及本機電子郵件用戶端的病毒掃描。</span><span class="sxs-lookup"><span data-stu-id="c40a6-166">Client add-in examples include reference add-ins for word processors, specialized features for graphics programs and games, and virus scanning for local e-mail clients.</span></span>  
  
 [<span data-ttu-id="c40a6-167">回到頁首</span><span class="sxs-lookup"><span data-stu-id="c40a6-167">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="c40a6-168">相關主題</span><span class="sxs-lookup"><span data-stu-id="c40a6-168">Related Topics</span></span>  
  
|<span data-ttu-id="c40a6-169">標題</span><span class="sxs-lookup"><span data-stu-id="c40a6-169">Title</span></span>|<span data-ttu-id="c40a6-170">描述</span><span class="sxs-lookup"><span data-stu-id="c40a6-170">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c40a6-171">Pipeline Development</span><span class="sxs-lookup"><span data-stu-id="c40a6-171">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)|<span data-ttu-id="c40a6-172">說明從主應用程式到增益集之區段的通訊管道。</span><span class="sxs-lookup"><span data-stu-id="c40a6-172">Describes the communication pipeline of segments from the host application to the add-in.</span></span> <span data-ttu-id="c40a6-173">提供逐步解說主題中的程式碼範例，說明如何建構管線，以及如何將區段部署至 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]中的管線。</span><span class="sxs-lookup"><span data-stu-id="c40a6-173">Provides code examples in walkthrough topics that describe how to construct the pipeline and how to deploy segments to the pipeline in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>|  
|[<span data-ttu-id="c40a6-174">應用程式定義域和組件</span><span class="sxs-lookup"><span data-stu-id="c40a6-174">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)|<span data-ttu-id="c40a6-175">說明應用程式定義域 (針對安全性、可靠性和版本控制提供隔離界限) 與組件之間的關係。</span><span class="sxs-lookup"><span data-stu-id="c40a6-175">Describes the relationship between application domains, which provide an isolation boundary for security, reliability, and versioning, and assemblies.</span></span>|  
  
 [<span data-ttu-id="c40a6-176">回到頁首</span><span class="sxs-lookup"><span data-stu-id="c40a6-176">Back to top</span></span>](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="c40a6-177">參考資料</span><span class="sxs-lookup"><span data-stu-id="c40a6-177">Reference</span></span>  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [<span data-ttu-id="c40a6-178">回到頁首</span><span class="sxs-lookup"><span data-stu-id="c40a6-178">Back to top</span></span>](#top)