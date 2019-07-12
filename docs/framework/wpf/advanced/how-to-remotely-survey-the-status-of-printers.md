---
title: 作法：從遠端調查印表機的狀態
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- surveying printer status remotely [WPF]
- printer status [WPF], surveying remotely
- remotely surveying printer status [WPF]
- status [WPF], printers [WPF], surveying remotely
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
ms.openlocfilehash: 4140152079b93e3c0a3d5fcda0e1b2c6f9fb89a4
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859858"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="a3317-102">作法：從遠端調查印表機的狀態</span><span class="sxs-lookup"><span data-stu-id="a3317-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="a3317-103">在任何時候，中型和大型公司都可能有多部印表機因為夾紙或紙張用完或一些其他問題狀況而無法運作。</span><span class="sxs-lookup"><span data-stu-id="a3317-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="a3317-104">一組豐富的公開 Api 的 Microsoft.NET Framework 中的印表機內容會提供方法來執行印表機狀態的快速問卷調查。</span><span class="sxs-lookup"><span data-stu-id="a3317-104">The rich set of printer properties exposed in the APIs of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3317-105">範例</span><span class="sxs-lookup"><span data-stu-id="a3317-105">Example</span></span>  
 <span data-ttu-id="a3317-106">建立這類公用程式的主要步驟如下所示。</span><span class="sxs-lookup"><span data-stu-id="a3317-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1. <span data-ttu-id="a3317-107">取得所有列印伺服器的清單。</span><span class="sxs-lookup"><span data-stu-id="a3317-107">Obtain a list of all print servers.</span></span>  
  
2. <span data-ttu-id="a3317-108">對伺服器執行迴圈，以查詢其列印佇列。</span><span class="sxs-lookup"><span data-stu-id="a3317-108">Loop through the servers to query their print queues.</span></span>  
  
3. <span data-ttu-id="a3317-109">在伺服器迴圈的每次操作中，對所有伺服器的佇列執行迴圈，並讀取可能表示佇列目前不在運作中的每個屬性。</span><span class="sxs-lookup"><span data-stu-id="a3317-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="a3317-110">下列程式碼是一系列的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="a3317-110">The code below is a series of snippets.</span></span> <span data-ttu-id="a3317-111">為了簡單起見，本範例假設有列印伺服器的 CRLF 分隔清單。</span><span class="sxs-lookup"><span data-stu-id="a3317-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="a3317-112">變數`fileOfPrintServers`是<xref:System.IO.StreamReader>這個檔案的物件。</span><span class="sxs-lookup"><span data-stu-id="a3317-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="a3317-113">由於每個伺服器名稱的那一行，呼叫的<xref:System.IO.StreamReader.ReadLine%2A>取得下一部伺服器的名稱，並將移<xref:System.IO.StreamReader>的下一行的開頭的資料指標。</span><span class="sxs-lookup"><span data-stu-id="a3317-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="a3317-114">外部迴圈中，在程式碼會建立<xref:System.Printing.PrintServer>最新的列印伺服器物件，並指定應用程式是以具有系統管理權限給伺服器。</span><span class="sxs-lookup"><span data-stu-id="a3317-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3317-115">如果有大量伺服器，您可以使用來改善效能<xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29>建構函式，只初始化，就需要的屬性。</span><span class="sxs-lookup"><span data-stu-id="a3317-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="a3317-116">然後此範例使用<xref:System.Printing.PrintServer.GetPrintQueues%2A>建立集合的所有伺服器的佇列，並開始循環使用它們。</span><span class="sxs-lookup"><span data-stu-id="a3317-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="a3317-117">此內部迴圈包含一個分支結構，其對應於檢查印表機狀態的兩種方法︰</span><span class="sxs-lookup"><span data-stu-id="a3317-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
- <span data-ttu-id="a3317-118">您可以閱讀的旗標<xref:System.Printing.PrintQueue.QueueStatus%2A>類型的屬性<xref:System.Printing.PrintQueueStatus>。</span><span class="sxs-lookup"><span data-stu-id="a3317-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
- <span data-ttu-id="a3317-119">您可以讀取每個相關的屬性，例如<xref:System.Printing.PrintQueue.IsOutOfPaper%2A>，和<xref:System.Printing.PrintQueue.IsPaperJammed%2A>。</span><span class="sxs-lookup"><span data-stu-id="a3317-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="a3317-120">此範例會示範這兩種方法，所以使用者先前已提示要使用的方法，且如果他或她想要使用的旗標，回應"y"<xref:System.Printing.PrintQueue.QueueStatus%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a3317-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if he or she wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="a3317-121">請參閱以下兩種方法的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a3317-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="a3317-122">最後，結果會呈現給使用者。</span><span class="sxs-lookup"><span data-stu-id="a3317-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="a3317-123">若要檢查印表機狀態使用的旗標<xref:System.Printing.PrintQueue.QueueStatus%2A>屬性，檢查以查看是否已設定每個相關旗標。</span><span class="sxs-lookup"><span data-stu-id="a3317-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="a3317-124">若要查看是否已在一組位元旗標中設定一個位元，標準方法就是以這組旗標做為一個運算元，而旗標本身做為另一個運算元來執行邏輯 AND 運算。</span><span class="sxs-lookup"><span data-stu-id="a3317-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="a3317-125">因為旗標本身只會設定一個位元，所以邏輯 AND 的結果是最多設定相同的位元。</span><span class="sxs-lookup"><span data-stu-id="a3317-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="a3317-126">若要查明是否如此，只要比較邏輯 AND 的結果與旗標本身。</span><span class="sxs-lookup"><span data-stu-id="a3317-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="a3317-127">如需詳細資訊，請參閱 < <xref:System.Printing.PrintQueueStatus>，則[& 運算子 (C#參考)](~/docs/csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)，和<xref:System.FlagsAttribute>。</span><span class="sxs-lookup"><span data-stu-id="a3317-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](~/docs/csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="a3317-128">對於已設定位元的每個屬性，程式碼會在將呈現給使用者的最終報告中加入注意事項。</span><span class="sxs-lookup"><span data-stu-id="a3317-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="a3317-129">(以下將討論在程式碼結尾呼叫的 **ReportAvailabilityAtThisTime** 方法。)</span><span class="sxs-lookup"><span data-stu-id="a3317-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="a3317-130">若要使用每個屬性來檢查印表機狀態，您只要讀取每個屬性，而如果屬性為 `true`，則在將呈現給使用者的最終報告中加入注意事項。</span><span class="sxs-lookup"><span data-stu-id="a3317-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="a3317-131">(以下將討論在程式碼結尾呼叫的 **ReportAvailabilityAtThisTime** 方法。)</span><span class="sxs-lookup"><span data-stu-id="a3317-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="a3317-132">已建立 **ReportAvailabilityAtThisTime** 方法，以防萬一您需要判斷目前是否可使用佇列。</span><span class="sxs-lookup"><span data-stu-id="a3317-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="a3317-133">此方法不會執行任何動作如果<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>和<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>屬性相等，因為在此情況下印表機可在所有的時間。</span><span class="sxs-lookup"><span data-stu-id="a3317-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="a3317-134">如果兩者不同，此方法會取得目前的時間，而後轉換成總分鐘數，因為<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>並<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>屬性是<xref:System.Int32>不代表之後午夜分鐘<xref:System.DateTime>物件。</span><span class="sxs-lookup"><span data-stu-id="a3317-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="a3317-135">最後，此方法會檢查目前的時間是否介於開始與「直到」時間之間。</span><span class="sxs-lookup"><span data-stu-id="a3317-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="a3317-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3317-136">See also</span></span>

- <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>
- <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>
- <xref:System.DateTime>
- <xref:System.Printing.PrintQueueStatus>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- [<span data-ttu-id="a3317-137">& 運算子 (C#參考)</span><span class="sxs-lookup"><span data-stu-id="a3317-137">& Operator (C# Reference)</span></span>](~/docs/csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [<span data-ttu-id="a3317-138">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="a3317-138">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="a3317-139">列印概觀</span><span class="sxs-lookup"><span data-stu-id="a3317-139">Printing Overview</span></span>](printing-overview.md)
