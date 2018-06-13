---
title: 文件核准程序
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: c28dafd3b0a1cb6dbee37fed2b3df8923ccd82c8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809488"
---
# <a name="document-approval-process"></a><span data-ttu-id="14437-102">文件核准程序</span><span class="sxs-lookup"><span data-stu-id="14437-102">Document Approval Process</span></span>
<span data-ttu-id="14437-103">這個範例會示範一起使用的 Windows Workflow Foundation (WF) 和 Windows Communication Foundation (WCF) 的許多功能。</span><span class="sxs-lookup"><span data-stu-id="14437-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="14437-104">結合這些功能來實作文件核准程序案例。</span><span class="sxs-lookup"><span data-stu-id="14437-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="14437-105">用戶端應用程式會提交文件以供核准，以及核准文件。</span><span class="sxs-lookup"><span data-stu-id="14437-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="14437-106">核准管理員應用程式是用來促進用戶端之間的通訊，以及強制執行核准程序的規則。</span><span class="sxs-lookup"><span data-stu-id="14437-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="14437-107">核准程序是可執行數個核准類型的工作流程。</span><span class="sxs-lookup"><span data-stu-id="14437-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="14437-108">活動是用來取得單一核准、仲裁核准 (核准者集合的百分比)，以及在序列中包含仲裁和單一核准的複雜核准程序。</span><span class="sxs-lookup"><span data-stu-id="14437-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="14437-109">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="14437-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="14437-110">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="14437-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="14437-111">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="14437-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="14437-112">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="14437-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a><span data-ttu-id="14437-113">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="14437-113">Sample Details</span></span>  
 <span data-ttu-id="14437-114">下圖示範此文件核准程序工作流程。</span><span class="sxs-lookup"><span data-stu-id="14437-114">The following graphic demonstrates the document approval process workflow.</span></span>  
  
 <span data-ttu-id="14437-115">![文件核准程序工作流程](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")</span><span class="sxs-lookup"><span data-stu-id="14437-115">![A document approval process workflow](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")</span></span>  
  
 <span data-ttu-id="14437-116">從用戶端的觀點來看，核准程序的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="14437-116">From the client's perspective, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="14437-117">用戶端在核准程序系統中訂閱成為使用者。</span><span class="sxs-lookup"><span data-stu-id="14437-117">A client subscribes to be a user in the approval process system.</span></span>  
  
2.  <span data-ttu-id="14437-118">WCF 用戶端傳送給核准管理員應用程式所裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="14437-118">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>  
  
3.  <span data-ttu-id="14437-119">唯一的使用者識別碼傳回至用戶端。</span><span class="sxs-lookup"><span data-stu-id="14437-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="14437-120">用戶端現在會參與核准程序。</span><span class="sxs-lookup"><span data-stu-id="14437-120">The client can now participate in approval processes.</span></span>  
  
4.  <span data-ttu-id="14437-121">一旦加入，用戶端可以使用單一核准、仲裁核准或複雜核准程序來傳送文件以供核准。</span><span class="sxs-lookup"><span data-stu-id="14437-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>  
  
5.  <span data-ttu-id="14437-122">按一下用戶端介面中的按鈕，在用戶端的工作流程服務主機中啟動工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="14437-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>  
  
6.  <span data-ttu-id="14437-123">工作流程傳送核准要求給核准管理員應用程式。</span><span class="sxs-lookup"><span data-stu-id="14437-123">The workflow sends an approval request to the approval manager application.</span></span>  
  
7.  <span data-ttu-id="14437-124">工作流程管理員在其一方啟動工作流程以代表核准程序。</span><span class="sxs-lookup"><span data-stu-id="14437-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>  
  
8.  <span data-ttu-id="14437-125">一旦管理員核准工作流程執行，將結果送回用戶端。</span><span class="sxs-lookup"><span data-stu-id="14437-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>  
  
9. <span data-ttu-id="14437-126">用戶端顯示結果。</span><span class="sxs-lookup"><span data-stu-id="14437-126">The client displays the results.</span></span>  
  
10. <span data-ttu-id="14437-127">用戶端隨時可能收到核准要求，並回應要求。</span><span class="sxs-lookup"><span data-stu-id="14437-127">A client may receive an approval request and respond to the request at any point in time.</span></span>  
  
11. <span data-ttu-id="14437-128">在用戶端上託管的 WCF 服務可以從核准管理員應用程式收到核准要求。</span><span class="sxs-lookup"><span data-stu-id="14437-128">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>  
  
12. <span data-ttu-id="14437-129">文件資訊在用戶端上呈現以供檢閱。</span><span class="sxs-lookup"><span data-stu-id="14437-129">The document information is presented on the client for review.</span></span>  
  
13. <span data-ttu-id="14437-130">使用者可以核准或拒絕文件。</span><span class="sxs-lookup"><span data-stu-id="14437-130">The user can approve or reject the document.</span></span>  
  
14. <span data-ttu-id="14437-131">WCF 用戶端用於傳送核准回應送回核准管理員應用程式。</span><span class="sxs-lookup"><span data-stu-id="14437-131">A WCF client is used to send an approval response back to the approval manager application.</span></span>  
  
 <span data-ttu-id="14437-132">從核准管理員應用程式的觀點來看，核准程序的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="14437-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>  
  
1.  <span data-ttu-id="14437-133">用戶端要求參與核准程序系統。</span><span class="sxs-lookup"><span data-stu-id="14437-133">A client requests to participate to the approval process system.</span></span>  
  
2.  <span data-ttu-id="14437-134">WCF 服務上核准管理員收到核准程序系統一部分的要求。</span><span class="sxs-lookup"><span data-stu-id="14437-134">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>  
  
3.  <span data-ttu-id="14437-135">產生用戶端的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="14437-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="14437-136">將使用者資訊儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="14437-136">The user information is stored in a database.</span></span>  
  
4.  <span data-ttu-id="14437-137">唯一的識別碼送回使用者。</span><span class="sxs-lookup"><span data-stu-id="14437-137">The unique ID is sent back to the user.</span></span>  
  
5.  <span data-ttu-id="14437-138">收到核准要求。</span><span class="sxs-lookup"><span data-stu-id="14437-138">An approval request is receive.</span></span> <span data-ttu-id="14437-139">核准管理員執行核准程序。</span><span class="sxs-lookup"><span data-stu-id="14437-139">The approval manager executes an approval process.</span></span>  
  
6.  <span data-ttu-id="14437-140">核准管理員收到核准要求，啟動新的工作流程。</span><span class="sxs-lookup"><span data-stu-id="14437-140">An approval request is received by the approval manager, starting a new workflow.</span></span>  
  
7.  <span data-ttu-id="14437-141">根據要求類型 (單一、仲裁或複雜)，執行不同的活動。</span><span class="sxs-lookup"><span data-stu-id="14437-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>  
  
8.  <span data-ttu-id="14437-142">具有相互關聯的 Send 和 Receive 活動用來將核准要求傳送至用戶端以供檢閱，以及傳送回應。</span><span class="sxs-lookup"><span data-stu-id="14437-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>  
  
9. <span data-ttu-id="14437-143">核准程序工作流程的結果傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="14437-143">The result of the approval process workflow is sent to the client.</span></span>  
  
## <a name="using-the-sample"></a><span data-ttu-id="14437-144">使用範例</span><span class="sxs-lookup"><span data-stu-id="14437-144">Using the Sample</span></span>  
  
##### <a name="to-set-up-the-database"></a><span data-ttu-id="14437-145">若要設定資料庫</span><span class="sxs-lookup"><span data-stu-id="14437-145">To set up the database</span></span>  
  
1.  <span data-ttu-id="14437-146">以系統管理員權限開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元視窗，然後瀏覽至此 DocumentApprovalProcess 資料夾，並執行 Setup.cmd。</span><span class="sxs-lookup"><span data-stu-id="14437-146">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>  
  
##### <a name="to-set-up-the-application"></a><span data-ttu-id="14437-147">若要設定應用程式</span><span class="sxs-lookup"><span data-stu-id="14437-147">To set up the application</span></span>  
  
1.  <span data-ttu-id="14437-148">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 DocumentApprovalProcess.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="14437-148">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DocumentApprovalProcess.sln solution file.</span></span>  
  
2.  <span data-ttu-id="14437-149">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="14437-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="14437-150">若要執行此方案，請啟動核准管理員應用程式中的 ApprovalManager 專案上按一下滑鼠右鍵**方案總管 中**按一下**偵錯**->**開始**從快顯功能表的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="14437-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>  
  
     <span data-ttu-id="14437-151">等候管理員輸出，通知已準備就緒。</span><span class="sxs-lookup"><span data-stu-id="14437-151">Wait for the manager’s output to let you know that it is ready.</span></span>  
  
##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="14437-152">若要執行單一核准案例</span><span class="sxs-lookup"><span data-stu-id="14437-152">To run the single approval scenario</span></span>  
  
1.  <span data-ttu-id="14437-153">以系統管理員權限開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="14437-153">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="14437-154">巡覽至包含方案的目錄。</span><span class="sxs-lookup"><span data-stu-id="14437-154">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="14437-155">巡覽至 ApprovalClient\Bin\Debug 資料夾，並執行兩個 ApprovalClient.exe 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14437-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="14437-156">按一下**探索**，等到**訂閱**按鈕啟用。</span><span class="sxs-lookup"><span data-stu-id="14437-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="14437-157">輸入任何使用者名稱，然後按一下**訂閱**。</span><span class="sxs-lookup"><span data-stu-id="14437-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="14437-158">對其中一個用戶端，使用 `UserType1`，對另一個輸入 `UserType2`。</span><span class="sxs-lookup"><span data-stu-id="14437-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="14437-159">在 `UserType1` 用戶端中，從下拉式功能表中選取單一核准類型，然後輸入文件名稱和內容。</span><span class="sxs-lookup"><span data-stu-id="14437-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="14437-160">按一下**要求核准**。</span><span class="sxs-lookup"><span data-stu-id="14437-160">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="14437-161">在 `UserType2` 用戶端中，待核准的文件隨即出現。</span><span class="sxs-lookup"><span data-stu-id="14437-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="14437-162">選取它，然後按**核准**或**拒絕**。</span><span class="sxs-lookup"><span data-stu-id="14437-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="14437-163">`UserType1` 用戶端中應該會顯示結果。</span><span class="sxs-lookup"><span data-stu-id="14437-163">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="14437-164">若要執行仲裁核准案例</span><span class="sxs-lookup"><span data-stu-id="14437-164">To run the quorum approval scenario</span></span>  
  
1.  <span data-ttu-id="14437-165">以系統管理員權限開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="14437-165">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="14437-166">巡覽至包含方案的目錄。</span><span class="sxs-lookup"><span data-stu-id="14437-166">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="14437-167">巡覽至 ApprovalClient\Bin\Debug 資料夾，並執行三個 ApprovalClient.exe 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14437-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="14437-168">按一下**探索**，等到**訂閱**按鈕啟用。</span><span class="sxs-lookup"><span data-stu-id="14437-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="14437-169">輸入任何使用者名稱，然後按一下**訂閱**。</span><span class="sxs-lookup"><span data-stu-id="14437-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="14437-170">對其中一個用戶端，使用 `UserType1`，對另外兩個輸入 `UserType2`。</span><span class="sxs-lookup"><span data-stu-id="14437-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>  
  
6.  <span data-ttu-id="14437-171">在 `UserType1` 用戶端中，從下拉式功能表中選取仲裁核准類型，然後輸入文件名稱和內容。</span><span class="sxs-lookup"><span data-stu-id="14437-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="14437-172">按一下**要求核准**。</span><span class="sxs-lookup"><span data-stu-id="14437-172">Click **Request Approval**.</span></span> <span data-ttu-id="14437-173">這會要求兩個 `UserType2` 用戶端核准或拒絕文件。</span><span class="sxs-lookup"><span data-stu-id="14437-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="14437-174">雖然兩個 `UserType2` 用戶端都必須回應，但是只要一個用戶端核准文件，文件就會獲得已核准狀態。</span><span class="sxs-lookup"><span data-stu-id="14437-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>  
  
7.  <span data-ttu-id="14437-175">在 `UserType2` 用戶端中，待核准的文件隨即出現。</span><span class="sxs-lookup"><span data-stu-id="14437-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="14437-176">選取它，然後按**核准**或**拒絕**。</span><span class="sxs-lookup"><span data-stu-id="14437-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="14437-177">`UserType1` 用戶端中應該會顯示結果。</span><span class="sxs-lookup"><span data-stu-id="14437-177">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="14437-178">若要執行複雜核准案例</span><span class="sxs-lookup"><span data-stu-id="14437-178">To run the complex approval scenario</span></span>  
  
1.  <span data-ttu-id="14437-179">以系統管理員權限開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="14437-179">Open a command prompt with administrator permission.</span></span>  
  
2.  <span data-ttu-id="14437-180">巡覽至包含方案的目錄。</span><span class="sxs-lookup"><span data-stu-id="14437-180">Navigate to the directory that contains the solution.</span></span>  
  
3.  <span data-ttu-id="14437-181">巡覽至 ApprovalClient\Bin\Debug 資料夾，並執行四個 ApprovalClient.exe 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14437-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>  
  
4.  <span data-ttu-id="14437-182">按一下**探索**，等到**訂閱**按鈕啟用。</span><span class="sxs-lookup"><span data-stu-id="14437-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5.  <span data-ttu-id="14437-183">輸入任何使用者名稱，然後按一下**訂閱**。</span><span class="sxs-lookup"><span data-stu-id="14437-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="14437-184">對其中一個用戶端，使用 `UserType1`，在兩個用戶端中輸入 `UserType2`，並在最後一個用戶端中使用 `UserType3`。</span><span class="sxs-lookup"><span data-stu-id="14437-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>  
  
6.  <span data-ttu-id="14437-185">在 `UserType1` 用戶端中，從下拉式功能表中選取單一核准類型，然後輸入文件名稱和內容。</span><span class="sxs-lookup"><span data-stu-id="14437-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="14437-186">按一下**要求核准**。</span><span class="sxs-lookup"><span data-stu-id="14437-186">Click **Request Approval**.</span></span>  
  
7.  <span data-ttu-id="14437-187">在 `UserType2` 用戶端中，待核准的文件隨即出現。</span><span class="sxs-lookup"><span data-stu-id="14437-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="14437-188">選取它，然後按**核准**，文件傳遞至`UserType3`用戶端。</span><span class="sxs-lookup"><span data-stu-id="14437-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>  
  
     <span data-ttu-id="14437-189">如果第一個 `UserType2` 仲裁核准文件，文件會傳遞至 `UserType3` 用戶端。</span><span class="sxs-lookup"><span data-stu-id="14437-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>  
  
8.  <span data-ttu-id="14437-190">從 `UserType3` 用戶端核准或拒絕文件。</span><span class="sxs-lookup"><span data-stu-id="14437-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="14437-191">`UserType1` 用戶端中應該會顯示結果。</span><span class="sxs-lookup"><span data-stu-id="14437-191">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-clean-up"></a><span data-ttu-id="14437-192">若要清除</span><span class="sxs-lookup"><span data-stu-id="14437-192">To clean up</span></span>  
  
1.  <span data-ttu-id="14437-193">從 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元，巡覽至 DocumentApprovalProcess 資料夾，並執行 Cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="14437-193">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>