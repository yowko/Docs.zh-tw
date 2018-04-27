---
title: 如何：得知列印工作是否可在此時列印
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eef74cfa290614e530fa22a34533c7924d4af1b4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a><span data-ttu-id="90e18-102">如何：得知列印工作是否可在此時列印</span><span class="sxs-lookup"><span data-stu-id="90e18-102">How to: Discover Whether a Print Job Can Be Printed At This Time of Day</span></span>
<span data-ttu-id="90e18-103">列印佇列並非永遠可用的一天 24 小時。</span><span class="sxs-lookup"><span data-stu-id="90e18-103">Print queues are not always available for 24 hours a day.</span></span> <span data-ttu-id="90e18-104">它們有可以設定讓它們無法使用在每天特定時間的開始和結束時間屬性。</span><span class="sxs-lookup"><span data-stu-id="90e18-104">They have start and end time properties that can be set to make them unavailable at certain times of day.</span></span> <span data-ttu-id="90e18-105">這項功能可用，例如，保留獨佔使用的特定部門下午 5 點後的印表機。</span><span class="sxs-lookup"><span data-stu-id="90e18-105">This feature can be used, for example, to reserve a printer for the exclusive use of a certain department after 5 P.M..</span></span> <span data-ttu-id="90e18-106">該部門會有不同的佇列服務的印表機，比其他部門使用。</span><span class="sxs-lookup"><span data-stu-id="90e18-106">That department would have a different queue servicing the printer than other departments use.</span></span> <span data-ttu-id="90e18-107">其他部門的佇列會被設定為無法使用下午 5 點後，佇列的偏好部門可能被設定為時隨時可用。</span><span class="sxs-lookup"><span data-stu-id="90e18-107">The queue for the other departments would be set to be unavailable after 5 P.M., while queue for the favored department could be set to be available at all times.</span></span>  
  
 <span data-ttu-id="90e18-108">此外，列印工作本身也可以設定為可列印只在指定的時間範圍內。</span><span class="sxs-lookup"><span data-stu-id="90e18-108">Moreover, print jobs themselves can be set to be printable only within a specified span of time.</span></span>  
  
 <span data-ttu-id="90e18-109"><xref:System.Printing.PrintQueue>和<xref:System.Printing.PrintSystemJobInfo>類別中公開[!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]Microsoft.NET framework 提供一種機制從遠端檢查指定的列印工作是否可以在目前的時間列印上指定的佇列。</span><span class="sxs-lookup"><span data-stu-id="90e18-109">The <xref:System.Printing.PrintQueue> and <xref:System.Printing.PrintSystemJobInfo> classes exposed in the [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] of Microsoft .NET Framework provide a means for remotely checking whether a given print job can print on a given queue at the current time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90e18-110">範例</span><span class="sxs-lookup"><span data-stu-id="90e18-110">Example</span></span>  
 <span data-ttu-id="90e18-111">下列範例是可以診斷問題的列印工作的範例。</span><span class="sxs-lookup"><span data-stu-id="90e18-111">The example below is a sample that can diagnose problems with a print job.</span></span>  
  
 <span data-ttu-id="90e18-112">有兩個主要步驟針對這類型的函式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="90e18-112">There are two major steps for this kind of function as follows.</span></span>  
  
1.  <span data-ttu-id="90e18-113">讀取<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>和<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>屬性<xref:System.Printing.PrintQueue>以判斷它們之間是否為目前的時間。</span><span class="sxs-lookup"><span data-stu-id="90e18-113">Read the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties of the <xref:System.Printing.PrintQueue> to determine whether the current time is between them.</span></span>  
  
2.  <span data-ttu-id="90e18-114">讀取<xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A>和<xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A>屬性<xref:System.Printing.PrintSystemJobInfo>以判斷它們之間是否為目前的時間。</span><span class="sxs-lookup"><span data-stu-id="90e18-114">Read the <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> and <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> properties of the <xref:System.Printing.PrintSystemJobInfo> to determine whether the current time is between them.</span></span>  
  
 <span data-ttu-id="90e18-115">但複雜性引起的事實，這些屬性不<xref:System.DateTime>物件。</span><span class="sxs-lookup"><span data-stu-id="90e18-115">But complications arise from the fact that these properties are not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="90e18-116">它們是改為<xref:System.Int32>express 一天的時間為午夜之後的分鐘數字的物件。</span><span class="sxs-lookup"><span data-stu-id="90e18-116">Instead they are <xref:System.Int32> objects that express the time of day as the number of minutes since midnight.</span></span> <span data-ttu-id="90e18-117">此外，這不是午夜中目前的時區，但午夜 UTC （國際標準時間）。</span><span class="sxs-lookup"><span data-stu-id="90e18-117">Moreover, this is not midnight in the current time zone, but midnight UTC (Coordinated Universal Time).</span></span>  
  
 <span data-ttu-id="90e18-118">第一個程式碼範例所呈現的靜態方法**ReportQueueAndJobAvailability**，傳遞<xref:System.Printing.PrintSystemJobInfo>，呼叫以判斷是否可以在目前列印工作的 helper 方法並不是，它可以列印時。</span><span class="sxs-lookup"><span data-stu-id="90e18-118">The first code example presents the static method **ReportQueueAndJobAvailability**, which is passed a <xref:System.Printing.PrintSystemJobInfo> and calls helper methods to determine whether the job can print at the current time and, if not, when it can print.</span></span> <span data-ttu-id="90e18-119">請注意，<xref:System.Printing.PrintQueue>未傳遞至方法。</span><span class="sxs-lookup"><span data-stu-id="90e18-119">Notice that a <xref:System.Printing.PrintQueue> is not passed to the method.</span></span> <span data-ttu-id="90e18-120">這是因為<xref:System.Printing.PrintSystemJobInfo>包含佇列中的參考其<xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="90e18-120">This is because the <xref:System.Printing.PrintSystemJobInfo> includes a reference to the queue in its <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> property.</span></span>  
  
 <span data-ttu-id="90e18-121">多載的次級的方法，包括**ReportAvailabilityAtThisTime**可採用任一方法<xref:System.Printing.PrintQueue>或<xref:System.Printing.PrintSystemJobInfo>做為參數。</span><span class="sxs-lookup"><span data-stu-id="90e18-121">The subordinate methods include the overloaded **ReportAvailabilityAtThisTime** method which can take either a <xref:System.Printing.PrintQueue> or a <xref:System.Printing.PrintSystemJobInfo> as a parameter.</span></span> <span data-ttu-id="90e18-122">另外還有**TimeConverter.ConvertToLocalHumanReadableTime**。</span><span class="sxs-lookup"><span data-stu-id="90e18-122">There is also a **TimeConverter.ConvertToLocalHumanReadableTime**.</span></span> <span data-ttu-id="90e18-123">以下將討論上述所有方法。</span><span class="sxs-lookup"><span data-stu-id="90e18-123">All of these methods are discussed below.</span></span>  
  
 <span data-ttu-id="90e18-124">**ReportQueueAndJobAvailability**方法一開始會檢查為佇列或列印工作，則無法使用這一次。</span><span class="sxs-lookup"><span data-stu-id="90e18-124">The **ReportQueueAndJobAvailability** method begins by checking to see if either the queue or the print job is unavailable at this time.</span></span> <span data-ttu-id="90e18-125">如果無法使用其中任一項時，它接著會查看佇列無法使用。</span><span class="sxs-lookup"><span data-stu-id="90e18-125">If either of them is unavailable, it then checks to see if the queue unavailable.</span></span> <span data-ttu-id="90e18-126">如果無法使用，該方法會回報這項事實並當佇列就可以使用一次的時間。</span><span class="sxs-lookup"><span data-stu-id="90e18-126">If it is not available, then the method reports this fact and the time when the queue will become available again.</span></span> <span data-ttu-id="90e18-127">接著它會檢查工作，並無法使用時，會報告在下一次跨越時就可進行列印。</span><span class="sxs-lookup"><span data-stu-id="90e18-127">It then checks the job and if it is unavailable, it reports the next time span when it when it can print.</span></span> <span data-ttu-id="90e18-128">最後，該方法會回報作業可以列印時的最早時間。</span><span class="sxs-lookup"><span data-stu-id="90e18-128">Finally, the method reports the earliest time when the job can print.</span></span> <span data-ttu-id="90e18-129">這是遵循兩次的更新版本。</span><span class="sxs-lookup"><span data-stu-id="90e18-129">This is the later of following two times.</span></span>  
  
-   <span data-ttu-id="90e18-130">列印佇列下一個可用的時間。</span><span class="sxs-lookup"><span data-stu-id="90e18-130">The time when the print queue is next available.</span></span>  
  
-   <span data-ttu-id="90e18-131">列印工作下一個可用的時間。</span><span class="sxs-lookup"><span data-stu-id="90e18-131">The time when the print job is next available.</span></span>  
  
 <span data-ttu-id="90e18-132">當 reporting 每天時間、<xref:System.DateTime.ToShortTimeString%2A>因為這個方法會抑制年、 月和日從輸出，也會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="90e18-132">When reporting times of day, the <xref:System.DateTime.ToShortTimeString%2A> method is also called because this method suppresses the years, months, and days from the output.</span></span> <span data-ttu-id="90e18-133">您無法將列印佇列或列印工作的可用性限制特定年、 月或日。</span><span class="sxs-lookup"><span data-stu-id="90e18-133">You cannot restrict the availability of either a print queue or a print job to particular years, months, or days.</span></span>  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 <span data-ttu-id="90e18-134">兩個多載的**ReportAvailabilityAtThisTime**方法除了之外完全相同的類型傳遞給它們，因此只有<xref:System.Printing.PrintQueue>版本會顯示如下。</span><span class="sxs-lookup"><span data-stu-id="90e18-134">The two overloads of the **ReportAvailabilityAtThisTime** method are identical except for the type passed to them, so only the <xref:System.Printing.PrintQueue> version is presented below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90e18-135">方法都是相同的但型別事實引發的問題，此範例不會建立泛型方法的原因**ReportAvailabilityAtThisTime\<T >**。</span><span class="sxs-lookup"><span data-stu-id="90e18-135">The fact that the methods are identical except for type raises the question of why the sample does not create a generic method **ReportAvailabilityAtThisTime\<T>**.</span></span> <span data-ttu-id="90e18-136">原因是這種方法必須具有的類別，限制**StartTimeOfDay**和**UntilTimeOfDay**只能限制為屬性的方法呼叫，但泛型方法單一類別和唯一類別同時<xref:System.Printing.PrintQueue>和<xref:System.Printing.PrintSystemJobInfo>在繼承樹狀結構是<xref:System.Printing.PrintSystemObject>具有任何這類屬性。</span><span class="sxs-lookup"><span data-stu-id="90e18-136">The reason is that such a method would have to be restricted to a class that has the **StartTimeOfDay** and **UntilTimeOfDay** properties that the method calls, but a generic method can only be restricted to a single class and the only class common to both <xref:System.Printing.PrintQueue> and <xref:System.Printing.PrintSystemJobInfo> in the inheritance tree is <xref:System.Printing.PrintSystemObject> which has no such properties.</span></span>  
  
 <span data-ttu-id="90e18-137">**ReportAvailabilityAtThisTime**方法 （在下列程式碼範例顯示） 一開始會初始化<xref:System.Boolean>sentinel 變數`true`。</span><span class="sxs-lookup"><span data-stu-id="90e18-137">The **ReportAvailabilityAtThisTime** method (presented in the code example below) begins by initializing a <xref:System.Boolean> sentinel variable to `true`.</span></span> <span data-ttu-id="90e18-138">它會重設為`false`，如果不是可用的佇列。</span><span class="sxs-lookup"><span data-stu-id="90e18-138">It will be reset to `false`, if the queue is not available.</span></span>  
  
 <span data-ttu-id="90e18-139">接下來，此方法會檢查是否要啟動和 「 之前 」 時間是否相同。</span><span class="sxs-lookup"><span data-stu-id="90e18-139">Next, the method checks to see if the start and "until" times are identical.</span></span> <span data-ttu-id="90e18-140">如有需要，佇列是一律可用，所以此方法會傳回`true`。</span><span class="sxs-lookup"><span data-stu-id="90e18-140">If they are, the queue is always available, so the method returns `true`.</span></span>  
  
 <span data-ttu-id="90e18-141">如果佇列不是可用的所有時間，此方法會使用靜態<xref:System.DateTime.UtcNow%2A>屬性來取得目前的時間，<xref:System.DateTime>物件。</span><span class="sxs-lookup"><span data-stu-id="90e18-141">If the queue is not available all the time, the method uses the static <xref:System.DateTime.UtcNow%2A> property to get the current time as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="90e18-142">(我們不需要本機時間因為<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>和<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>屬性本身是以 UTC 時間。)</span><span class="sxs-lookup"><span data-stu-id="90e18-142">(We do not need local time because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are themselves in UTC time.)</span></span>  
  
 <span data-ttu-id="90e18-143">不過，這兩個屬性都不<xref:System.DateTime>物件。</span><span class="sxs-lookup"><span data-stu-id="90e18-143">However, these two properties are not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="90e18-144">它們是<xref:System.Int32>分鐘之後 UTC 午夜的數字來表示時間的 s。</span><span class="sxs-lookup"><span data-stu-id="90e18-144">They are <xref:System.Int32>s expressing the time as the number of minutes-after-UTC-midnight.</span></span> <span data-ttu-id="90e18-145">讓我們沒有轉換我們<xref:System.DateTime>分鐘之後午夜的物件。</span><span class="sxs-lookup"><span data-stu-id="90e18-145">So we do have to convert our <xref:System.DateTime> object to minutes-after-midnight.</span></span> <span data-ttu-id="90e18-146">完成時，方法只會檢查以查看是否 「 現在 」 是佇列的開始之間和 「 之前 」 時間，設定為 false，如果 「 現在 」 sentinel 不是，兩個時間之間，並傳回 sentinel。</span><span class="sxs-lookup"><span data-stu-id="90e18-146">When that is done, the method simply checks to see whether "now" is between the queue's start and "until" times, sets the sentinel to false if "now" is not between the two times, and returns the sentinel.</span></span>  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 <span data-ttu-id="90e18-147">**TimeConverter.ConvertToLocalHumanReadableTime** （顯示在下列程式碼範例） 的方法不會使用所導入的 Microsoft.NET Framework，因此討論是簡短的任何方法。</span><span class="sxs-lookup"><span data-stu-id="90e18-147">The **TimeConverter.ConvertToLocalHumanReadableTime** method (presented in the code example below) does not use any methods introduced with Microsoft .NET Framework, so the discussion is brief.</span></span> <span data-ttu-id="90e18-148">方法具有雙重轉換工作： 它必須採用整數來表示分鐘之後午夜，並將它轉換成人們可讀取的時間，它必須轉換為本地時間。</span><span class="sxs-lookup"><span data-stu-id="90e18-148">The method has a double conversion task: it must take an integer expressing minutes-after-midnight and convert it to a human-readable time and it must convert this to the local time.</span></span> <span data-ttu-id="90e18-149">其達成方式是先建立<xref:System.DateTime>物件，會設定為 UTC，然後它會使用的午夜<xref:System.DateTime.AddMinutes%2A>方法，將跟著傳遞至此方法的分鐘數。</span><span class="sxs-lookup"><span data-stu-id="90e18-149">It accomplishes this by first creating a <xref:System.DateTime> object that is set to midnight UTC and then it uses the <xref:System.DateTime.AddMinutes%2A> method to add the minutes that were passed to the method.</span></span> <span data-ttu-id="90e18-150">這會傳回新<xref:System.DateTime>表示傳遞給方法的原始時間。</span><span class="sxs-lookup"><span data-stu-id="90e18-150">This returns a new <xref:System.DateTime> expressing the original time that was passed to the method.</span></span> <span data-ttu-id="90e18-151"><xref:System.DateTime.ToLocalTime%2A>方法接著會將此轉換本地時間。</span><span class="sxs-lookup"><span data-stu-id="90e18-151">The <xref:System.DateTime.ToLocalTime%2A> method then converts this to local time.</span></span>  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a><span data-ttu-id="90e18-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90e18-152">See Also</span></span>  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintSystemJobInfo>  
 <xref:System.Printing.PrintQueue>  
 [<span data-ttu-id="90e18-153">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="90e18-153">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="90e18-154">列印概觀</span><span class="sxs-lookup"><span data-stu-id="90e18-154">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
