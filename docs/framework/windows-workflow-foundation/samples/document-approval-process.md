---
title: 文件核准程序
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: dfc2e0a12d053733823427ac50066b1e4a0f97aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005107"
---
# <a name="document-approval-process"></a><span data-ttu-id="ff43e-102">文件核准程序</span><span class="sxs-lookup"><span data-stu-id="ff43e-102">Document Approval Process</span></span>
<span data-ttu-id="ff43e-103">這個範例會示範一起使用的許多 Windows Workflow Foundation (WF) 和 Windows Communication Foundation (WCF) 的功能。</span><span class="sxs-lookup"><span data-stu-id="ff43e-103">This sample demonstrates the use of many Windows Workflow Foundation (WF) and Windows Communication Foundation (WCF) features together.</span></span> <span data-ttu-id="ff43e-104">結合這些功能來實作文件核准程序案例。</span><span class="sxs-lookup"><span data-stu-id="ff43e-104">Together they implement a document approval process scenario.</span></span> <span data-ttu-id="ff43e-105">用戶端應用程式會提交文件以供核准，以及核准文件。</span><span class="sxs-lookup"><span data-stu-id="ff43e-105">A client application can submit documents for approval and approve documents.</span></span> <span data-ttu-id="ff43e-106">核准管理員應用程式是用來促進用戶端之間的通訊，以及強制執行核准程序的規則。</span><span class="sxs-lookup"><span data-stu-id="ff43e-106">An approval manager application exists to facilitate communications between clients and to enforce the rules of the approval process.</span></span> <span data-ttu-id="ff43e-107">核准程序是可執行數個核准類型的工作流程。</span><span class="sxs-lookup"><span data-stu-id="ff43e-107">The approval process is a workflow that can execute several types of approval.</span></span> <span data-ttu-id="ff43e-108">活動是用來取得單一核准、仲裁核准 (核准者集合的百分比)，以及在序列中包含仲裁和單一核准的複雜核准程序。</span><span class="sxs-lookup"><span data-stu-id="ff43e-108">Activities exist to get a single approval, a quorum approval (a percentage of set of approvers), and a complex approval process that consists of a quorum and single approval in a sequence.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ff43e-109">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ff43e-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ff43e-110">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ff43e-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ff43e-111">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="ff43e-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff43e-112">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ff43e-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a><span data-ttu-id="ff43e-113">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="ff43e-113">Sample Details</span></span>  
 <span data-ttu-id="ff43e-114">下圖示範文件核准程序工作流程：</span><span class="sxs-lookup"><span data-stu-id="ff43e-114">The following graphic demonstrates the document approval process workflow:</span></span>  
  
 ![文件核准程序工作流程](./media/document-approval-process/document-approval-process.jpg)  
  
 <span data-ttu-id="ff43e-116">從用戶端的觀點來看，核准程序的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="ff43e-116">From the client's perspective, the approval process functions as follows:</span></span>  
  
1. <span data-ttu-id="ff43e-117">用戶端在核准程序系統中訂閱成為使用者。</span><span class="sxs-lookup"><span data-stu-id="ff43e-117">A client subscribes to be a user in the approval process system.</span></span>  
  
2. <span data-ttu-id="ff43e-118">WCF 用戶端會傳送至核准管理員應用程式所裝載的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="ff43e-118">A WCF client sends to a WCF service hosted by the approval manager application.</span></span>  
  
3. <span data-ttu-id="ff43e-119">唯一的使用者識別碼傳回至用戶端。</span><span class="sxs-lookup"><span data-stu-id="ff43e-119">A unique user ID is returned to the client.</span></span> <span data-ttu-id="ff43e-120">用戶端現在會參與核准程序。</span><span class="sxs-lookup"><span data-stu-id="ff43e-120">The client can now participate in approval processes.</span></span>  
  
4. <span data-ttu-id="ff43e-121">一旦加入，用戶端可以使用單一核准、仲裁核准或複雜核准程序來傳送文件以供核准。</span><span class="sxs-lookup"><span data-stu-id="ff43e-121">Once joined, a client can send a document for approval using single, quorum or complex approval processes.</span></span>  
  
5. <span data-ttu-id="ff43e-122">按一下用戶端介面中的按鈕，在用戶端的工作流程服務主機中啟動工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff43e-122">A button in the client’s interface is clicked, starting a workflow instance in a client Workflow Service Host.</span></span>  
  
6. <span data-ttu-id="ff43e-123">工作流程傳送核准要求給核准管理員應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff43e-123">The workflow sends an approval request to the approval manager application.</span></span>  
  
7. <span data-ttu-id="ff43e-124">工作流程管理員在其一方啟動工作流程以代表核准程序。</span><span class="sxs-lookup"><span data-stu-id="ff43e-124">The workflow manager starts a workflow on its own side to represent an approval process.</span></span>  
  
8. <span data-ttu-id="ff43e-125">一旦管理員核准工作流程執行，將結果送回用戶端。</span><span class="sxs-lookup"><span data-stu-id="ff43e-125">Once the manager approval workflow executes, the results are sent back to the client.</span></span>  
  
9. <span data-ttu-id="ff43e-126">用戶端顯示結果。</span><span class="sxs-lookup"><span data-stu-id="ff43e-126">The client displays the results.</span></span>  
  
10. <span data-ttu-id="ff43e-127">用戶端隨時可能收到核准要求，並回應要求。</span><span class="sxs-lookup"><span data-stu-id="ff43e-127">A client may receive an approval request and respond to the request at any point in time.</span></span>  
  
11. <span data-ttu-id="ff43e-128">在用戶端上裝載的 WCF 服務可以從核准管理員應用程式收到核准要求。</span><span class="sxs-lookup"><span data-stu-id="ff43e-128">A WCF service hosted on the client can receive an approval request from the approval manager application.</span></span>  
  
12. <span data-ttu-id="ff43e-129">文件資訊在用戶端上呈現以供檢閱。</span><span class="sxs-lookup"><span data-stu-id="ff43e-129">The document information is presented on the client for review.</span></span>  
  
13. <span data-ttu-id="ff43e-130">使用者可以核准或拒絕文件。</span><span class="sxs-lookup"><span data-stu-id="ff43e-130">The user can approve or reject the document.</span></span>  
  
14. <span data-ttu-id="ff43e-131">WCF 用戶端用來傳送核准回應送回核准管理員應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff43e-131">A WCF client is used to send an approval response back to the approval manager application.</span></span>  
  
 <span data-ttu-id="ff43e-132">從核准管理員應用程式的觀點來看，核准程序的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="ff43e-132">From the approval manager application’s point of view, the approval process functions as follows:</span></span>  
  
1. <span data-ttu-id="ff43e-133">用戶端要求參與核准程序系統。</span><span class="sxs-lookup"><span data-stu-id="ff43e-133">A client requests to participate to the approval process system.</span></span>  
  
2. <span data-ttu-id="ff43e-134">WCF 服務的核准管理員收到核准程序系統一部分的要求。</span><span class="sxs-lookup"><span data-stu-id="ff43e-134">A WCF service on the approval manager receives a request to be part of the approval process system.</span></span>  
  
3. <span data-ttu-id="ff43e-135">產生用戶端的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="ff43e-135">A unique ID is generated for the client.</span></span> <span data-ttu-id="ff43e-136">將使用者資訊儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="ff43e-136">The user information is stored in a database.</span></span>  
  
4. <span data-ttu-id="ff43e-137">唯一的識別碼送回使用者。</span><span class="sxs-lookup"><span data-stu-id="ff43e-137">The unique ID is sent back to the user.</span></span>  
  
5. <span data-ttu-id="ff43e-138">收到核准要求。</span><span class="sxs-lookup"><span data-stu-id="ff43e-138">An approval request is receive.</span></span> <span data-ttu-id="ff43e-139">核准管理員執行核准程序。</span><span class="sxs-lookup"><span data-stu-id="ff43e-139">The approval manager executes an approval process.</span></span>  
  
6. <span data-ttu-id="ff43e-140">核准管理員收到核准要求，啟動新的工作流程。</span><span class="sxs-lookup"><span data-stu-id="ff43e-140">An approval request is received by the approval manager, starting a new workflow.</span></span>  
  
7. <span data-ttu-id="ff43e-141">根據要求類型 (單一、仲裁或複雜)，執行不同的活動。</span><span class="sxs-lookup"><span data-stu-id="ff43e-141">Depending on the type of request (simple, quorum, or complex) a different activity is executed.</span></span>  
  
8. <span data-ttu-id="ff43e-142">具有相互關聯的 Send 和 Receive 活動用來將核准要求傳送至用戶端以供檢閱，以及傳送回應。</span><span class="sxs-lookup"><span data-stu-id="ff43e-142">Send and Receive activities with correlation are used to send the approval request to the client for review and receive the response.</span></span>  
  
9. <span data-ttu-id="ff43e-143">核准程序工作流程的結果傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="ff43e-143">The result of the approval process workflow is sent to the client.</span></span>  
  
## <a name="using-the-sample"></a><span data-ttu-id="ff43e-144">使用範例</span><span class="sxs-lookup"><span data-stu-id="ff43e-144">Using the Sample</span></span>  
  
##### <a name="to-set-up-the-database"></a><span data-ttu-id="ff43e-145">若要設定資料庫</span><span class="sxs-lookup"><span data-stu-id="ff43e-145">To set up the database</span></span>  
  
1. <span data-ttu-id="ff43e-146">從系統管理員權限開啟的 Visual Studio 2010 命令提示字元，瀏覽至此 DocumentApprovalProcess 資料夾，並執行 Setup.cmd。</span><span class="sxs-lookup"><span data-stu-id="ff43e-146">From a Visual Studio 2010 command prompt opened with Administrator privileges, navigate to this DocumentApprovalProcess folder and run Setup.cmd.</span></span>  
  
##### <a name="to-set-up-the-application"></a><span data-ttu-id="ff43e-147">若要設定應用程式</span><span class="sxs-lookup"><span data-stu-id="ff43e-147">To set up the application</span></span>  
  
1. <span data-ttu-id="ff43e-148">使用 Visual Studio 2010 開啟 DocumentApprovalProcess.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="ff43e-148">Using Visual Studio 2010, open the DocumentApprovalProcess.sln solution file.</span></span>  
  
2. <span data-ttu-id="ff43e-149">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="ff43e-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="ff43e-150">若要執行方案，請啟動核准管理員應用程式中的 ApprovalManager 專案上按一下滑鼠右鍵**方案總管**，然後按一下**偵錯**->**開始**從快顯功能表的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff43e-150">To run the solution, launch the Approval Manager Application by right-clicking the ApprovalManager project in the **Solution Explorer** and clicking **Debug**->**Start** new instance from the right-click menu.</span></span>  
  
     <span data-ttu-id="ff43e-151">等候管理員輸出，通知已準備就緒。</span><span class="sxs-lookup"><span data-stu-id="ff43e-151">Wait for the manager’s output to let you know that it is ready.</span></span>  
  
##### <a name="to-run-the-single-approval-scenario"></a><span data-ttu-id="ff43e-152">若要執行單一核准案例</span><span class="sxs-lookup"><span data-stu-id="ff43e-152">To run the single approval scenario</span></span>  
  
1. <span data-ttu-id="ff43e-153">以系統管理員權限開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ff43e-153">Open a command prompt with administrator permission.</span></span>  
  
2. <span data-ttu-id="ff43e-154">巡覽至包含方案的目錄。</span><span class="sxs-lookup"><span data-stu-id="ff43e-154">Navigate to the directory that contains the solution.</span></span>  
  
3. <span data-ttu-id="ff43e-155">巡覽至 ApprovalClient\Bin\Debug 資料夾，並執行兩個 ApprovalClient.exe 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff43e-155">Navigate to the ApprovalClient\Bin\Debug folder and execute two instances of ApprovalClient.exe.</span></span>  
  
4. <span data-ttu-id="ff43e-156">按一下 **探索**，等到**訂閱**按鈕已啟用。</span><span class="sxs-lookup"><span data-stu-id="ff43e-156">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5. <span data-ttu-id="ff43e-157">輸入任何使用者名稱，然後按一下**訂閱**。</span><span class="sxs-lookup"><span data-stu-id="ff43e-157">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="ff43e-158">對其中一個用戶端，使用 `UserType1`，對另一個輸入 `UserType2`。</span><span class="sxs-lookup"><span data-stu-id="ff43e-158">For one client, use `UserType1` and the other type `UserType2`.</span></span>  
  
6. <span data-ttu-id="ff43e-159">在 `UserType1` 用戶端中，從下拉式功能表中選取單一核准類型，然後輸入文件名稱和內容。</span><span class="sxs-lookup"><span data-stu-id="ff43e-159">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="ff43e-160">按一下 **要求核准**。</span><span class="sxs-lookup"><span data-stu-id="ff43e-160">Click **Request Approval**.</span></span>  
  
7. <span data-ttu-id="ff43e-161">在 `UserType2` 用戶端中，待核准的文件隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ff43e-161">In the `UserType2` client, a document awaiting approval appears.</span></span> <span data-ttu-id="ff43e-162">選取它，然後按**核准**或是**拒絕**。</span><span class="sxs-lookup"><span data-stu-id="ff43e-162">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="ff43e-163">`UserType1` 用戶端中應該會顯示結果。</span><span class="sxs-lookup"><span data-stu-id="ff43e-163">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-quorum-approval-scenario"></a><span data-ttu-id="ff43e-164">若要執行仲裁核准案例</span><span class="sxs-lookup"><span data-stu-id="ff43e-164">To run the quorum approval scenario</span></span>  
  
1. <span data-ttu-id="ff43e-165">以系統管理員權限開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ff43e-165">Open a command prompt with administrator permission.</span></span>  
  
2. <span data-ttu-id="ff43e-166">巡覽至包含方案的目錄。</span><span class="sxs-lookup"><span data-stu-id="ff43e-166">Navigate to the directory that contains the solution.</span></span>  
  
3. <span data-ttu-id="ff43e-167">巡覽至 ApprovalClient\Bin\Debug 資料夾，並執行三個 ApprovalClient.exe 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff43e-167">Navigate to the ApprovalClient\Bin\Debug folder and execute three instances of ApprovalClient.exe.</span></span>  
  
4. <span data-ttu-id="ff43e-168">按一下 **探索**，等到**訂閱**按鈕已啟用。</span><span class="sxs-lookup"><span data-stu-id="ff43e-168">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5. <span data-ttu-id="ff43e-169">輸入任何使用者名稱，然後按一下**訂閱**。</span><span class="sxs-lookup"><span data-stu-id="ff43e-169">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="ff43e-170">對其中一個用戶端，使用 `UserType1`，對另外兩個輸入 `UserType2`。</span><span class="sxs-lookup"><span data-stu-id="ff43e-170">For one client use `UserType1` and the other two type `UserType2`.</span></span>  
  
6. <span data-ttu-id="ff43e-171">在 `UserType1` 用戶端中，從下拉式功能表中選取仲裁核准類型，然後輸入文件名稱和內容。</span><span class="sxs-lookup"><span data-stu-id="ff43e-171">In the `UserType1` client, select the quorum approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="ff43e-172">按一下 **要求核准**。</span><span class="sxs-lookup"><span data-stu-id="ff43e-172">Click **Request Approval**.</span></span> <span data-ttu-id="ff43e-173">這會要求兩個 `UserType2` 用戶端核准或拒絕文件。</span><span class="sxs-lookup"><span data-stu-id="ff43e-173">This requests that the two `UserType2` clients approve or reject the document.</span></span> <span data-ttu-id="ff43e-174">雖然兩個 `UserType2` 用戶端都必須回應，但是只要一個用戶端核准文件，文件就會獲得已核准狀態。</span><span class="sxs-lookup"><span data-stu-id="ff43e-174">While both `UserType2` clients must respond, only one client must approve the document for it to be approved.</span></span>  
  
7. <span data-ttu-id="ff43e-175">在 `UserType2` 用戶端中，待核准的文件隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ff43e-175">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="ff43e-176">選取它，然後按**核准**或是**拒絕**。</span><span class="sxs-lookup"><span data-stu-id="ff43e-176">Select it and press **approve** or **reject**.</span></span> <span data-ttu-id="ff43e-177">`UserType1` 用戶端中應該會顯示結果。</span><span class="sxs-lookup"><span data-stu-id="ff43e-177">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-run-the-complex-approval-scenario"></a><span data-ttu-id="ff43e-178">若要執行複雜核准案例</span><span class="sxs-lookup"><span data-stu-id="ff43e-178">To run the complex approval scenario</span></span>  
  
1. <span data-ttu-id="ff43e-179">以系統管理員權限開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ff43e-179">Open a command prompt with administrator permission.</span></span>  
  
2. <span data-ttu-id="ff43e-180">巡覽至包含方案的目錄。</span><span class="sxs-lookup"><span data-stu-id="ff43e-180">Navigate to the directory that contains the solution.</span></span>  
  
3. <span data-ttu-id="ff43e-181">巡覽至 ApprovalClient\Bin\Debug 資料夾，並執行四個 ApprovalClient.exe 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff43e-181">Navigate to the ApprovalClient\Bin\Debug folder and execute four instances of ApprovalClient.exe.</span></span>  
  
4. <span data-ttu-id="ff43e-182">按一下 **探索**，等到**訂閱**按鈕已啟用。</span><span class="sxs-lookup"><span data-stu-id="ff43e-182">Click **discover**, wait until the **subscribe** button is enabled.</span></span>  
  
5. <span data-ttu-id="ff43e-183">輸入任何使用者名稱，然後按一下**訂閱**。</span><span class="sxs-lookup"><span data-stu-id="ff43e-183">Type any user name and click **subscribe**.</span></span> <span data-ttu-id="ff43e-184">對其中一個用戶端，使用 `UserType1`，在兩個用戶端中輸入 `UserType2`，並在最後一個用戶端中使用 `UserType3`。</span><span class="sxs-lookup"><span data-stu-id="ff43e-184">For one client use `UserType1`, in two uses type `UserType2`, and in the last use `UserType3`.</span></span>  
  
6. <span data-ttu-id="ff43e-185">在 `UserType1` 用戶端中，從下拉式功能表中選取單一核准類型，然後輸入文件名稱和內容。</span><span class="sxs-lookup"><span data-stu-id="ff43e-185">In the `UserType1` client, select the single approval type from the drop down menu and type a document name and content.</span></span> <span data-ttu-id="ff43e-186">按一下 **要求核准**。</span><span class="sxs-lookup"><span data-stu-id="ff43e-186">Click **Request Approval**.</span></span>  
  
7. <span data-ttu-id="ff43e-187">在 `UserType2` 用戶端中，待核准的文件隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ff43e-187">In the `UserType2` clients, a document awaiting approval appears.</span></span> <span data-ttu-id="ff43e-188">選取它，然後按**核准**，在文件傳遞至`UserType3`用戶端。</span><span class="sxs-lookup"><span data-stu-id="ff43e-188">Select it and press **approve**, the document is passed to the `UserType3` client.</span></span>  
  
     <span data-ttu-id="ff43e-189">如果第一個 `UserType2` 仲裁核准文件，文件會傳遞至 `UserType3` 用戶端。</span><span class="sxs-lookup"><span data-stu-id="ff43e-189">If the document is approved by the first `UserType2` quorum, the document is passed to the `UserType3` client.</span></span>  
  
8. <span data-ttu-id="ff43e-190">從 `UserType3` 用戶端核准或拒絕文件。</span><span class="sxs-lookup"><span data-stu-id="ff43e-190">Approve or reject the document from the `UserType3` client.</span></span> <span data-ttu-id="ff43e-191">`UserType1` 用戶端中應該會顯示結果。</span><span class="sxs-lookup"><span data-stu-id="ff43e-191">The results should show in the `UserType1` client.</span></span>  
  
##### <a name="to-clean-up"></a><span data-ttu-id="ff43e-192">若要清除</span><span class="sxs-lookup"><span data-stu-id="ff43e-192">To clean up</span></span>  
  
1. <span data-ttu-id="ff43e-193">在 Visual Studio 2010 命令提示字元中，巡覽至 DocumentApprovalProcess 資料夾，並執行 Cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="ff43e-193">From a Visual Studio 2010 command prompt, navigate to the DocumentApprovalProcess folder and run Cleanup.cmd.</span></span>
