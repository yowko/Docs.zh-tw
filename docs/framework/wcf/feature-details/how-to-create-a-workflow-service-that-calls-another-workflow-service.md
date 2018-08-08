---
title: HOW TO：建立會呼叫其他工作流程服務的工作流程服務
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: fda5a7286c3d20c7cdc2093e58bfe3fbdcf1d1c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497187"
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a><span data-ttu-id="557e7-102">HOW TO：建立會呼叫其他工作流程服務的工作流程服務</span><span class="sxs-lookup"><span data-stu-id="557e7-102">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>
<span data-ttu-id="557e7-103">有時工作流程服務需要從另一個工作流程服務取得資訊。</span><span class="sxs-lookup"><span data-stu-id="557e7-103">It is sometimes necessary for a workflow service to obtain information from another workflow service.</span></span>  <span data-ttu-id="557e7-104">本主題示範如何從另一個工作流程服務呼叫某個工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="557e7-104">This topic demonstrates how to call one workflow service from another.</span></span> <span data-ttu-id="557e7-105">在本主題中，我們會建立兩個工作流程服務，其中一個服務的方法會反轉輸入字串，而另一個服務則會在反轉使用第一個服務的字串之後，將輸入字串轉換成大寫。</span><span class="sxs-lookup"><span data-stu-id="557e7-105">In this topic, we’ll create two workflow services; one that has a method that reverses the input string, and another that converts the input string to uppercase after reversing the string that uses the first service.</span></span>  
  
### <a name="to-create-the-reverser-workflow-service"></a><span data-ttu-id="557e7-106">若要建立 Reverser 工作流程服務</span><span class="sxs-lookup"><span data-stu-id="557e7-106">To create the Reverser workflow service</span></span>  
  
1.  <span data-ttu-id="557e7-107">以系統管理員身分執行 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="557e7-107">Run [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] as an administrator.</span></span>  
  
2.  <span data-ttu-id="557e7-108">選取**檔案**，**新專案**。</span><span class="sxs-lookup"><span data-stu-id="557e7-108">Select **File**, **New Project**.</span></span> <span data-ttu-id="557e7-109">在下**工作流程**節點**已安裝的範本**窗格中，選取**WCF 工作流程服務應用程式**。</span><span class="sxs-lookup"><span data-stu-id="557e7-109">Under the **Workflow** node in the **Installed Templates** pane, select **WCF Workflow Service Application**.</span></span> <span data-ttu-id="557e7-110">將方案命名`NestedServices`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="557e7-110">Name the solution `NestedServices` and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="557e7-111">在下**伺服器**，請確定**使用本機 IIS Web 伺服器**已選取。</span><span class="sxs-lookup"><span data-stu-id="557e7-111">Under **Servers**, make sure that **Use Local IIS Web Server** is selected.</span></span> <span data-ttu-id="557e7-112">按一下**建立虛擬目錄**。</span><span class="sxs-lookup"><span data-stu-id="557e7-112">Click **Create Virtual Directory**.</span></span> <span data-ttu-id="557e7-113">按一下**確定**對話方塊方塊，指出已成功建立虛擬目錄中。</span><span class="sxs-lookup"><span data-stu-id="557e7-113">Click **OK** in the dialog box stating that the virtual directory was successfully created.</span></span>  
  
4.  <span data-ttu-id="557e7-114">在 [方案總管] 中，將 Service1.xamlx 重新命名以`StringReverserService.xamlx`。</span><span class="sxs-lookup"><span data-stu-id="557e7-114">In Solution Explorer, rename Service1.xamlx to `StringReverserService.xamlx`.</span></span>  
  
5.  <span data-ttu-id="557e7-115">在**專案屬性**新專案的頁面上，按一下**Web**  索引標籤。設定**起始動作**至**特定頁面**，並選取 StringReverserService.xamlx 當做起始頁面。</span><span class="sxs-lookup"><span data-stu-id="557e7-115">On the **Project Properties** page for the new project, click the **Web** tab. Set the **Start Action** to **Specific Page**, and select StringReverserService.xamlx as the page to start.</span></span>  
  
6.  <span data-ttu-id="557e7-116">在設計工具中開啟 StringReverserService.xamlx 並刪除現有的 `ReceiveRequest` 和 `SendReply` 活動，然後將 `ReceiveAndSendReply` 活動拖曳到現有的序列活動中。</span><span class="sxs-lookup"><span data-stu-id="557e7-116">Open StringReverserService.xamlx in the designer and delete the existing `ReceiveRequest` and `SendReply` activities, and then drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>  
  
    1.  <span data-ttu-id="557e7-117">設定**OperationName**為 ReverseString。</span><span class="sxs-lookup"><span data-stu-id="557e7-117">Set the **OperationName** to ReverseString.</span></span>  
  
    2.  <span data-ttu-id="557e7-118">設定**ServiceContractName**  設定為 IReverseString。</span><span class="sxs-lookup"><span data-stu-id="557e7-118">Set the **ServiceContractName** to IReverseString.</span></span>  
  
    3.  <span data-ttu-id="557e7-119">選取**CanCreateInstance**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="557e7-119">Select the **CanCreateInstance** check box.</span></span>  
  
7.  <span data-ttu-id="557e7-120">選取**SequentialService**活動，然後再按一下**變數**設計工具底部的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="557e7-120">Select the **SequentialService** activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="557e7-121">建立兩個新的變數，其名稱分別是 String 型別的 StringToReverse 和 ReversedStringToReturn。</span><span class="sxs-lookup"><span data-stu-id="557e7-121">Create two new variables named StringToReverse and ReversedStringToReturn of type String.</span></span>  
  
8.  <span data-ttu-id="557e7-122">按一下**定義**中連結**接收**活動。</span><span class="sxs-lookup"><span data-stu-id="557e7-122">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="557e7-123">按一下**參數**，並建立名為 InputString 會指派給 StringToReverse 的 String 型別參數。</span><span class="sxs-lookup"><span data-stu-id="557e7-123">Click the  **Parameters**, and create a parameter named InputString of type String that assigns to StringToReverse.</span></span>  
  
9. <span data-ttu-id="557e7-124">按一下**定義**中連結**SendReplyToReceive**活動。</span><span class="sxs-lookup"><span data-stu-id="557e7-124">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="557e7-125">按一下**參數**，並建立名為 ReversedString String 型別，指派給 ReversedStringToReturn 參數。</span><span class="sxs-lookup"><span data-stu-id="557e7-125">Click the **Parameters**, and create a parameter named ReversedString of type String, assigned to ReversedStringToReturn.</span></span>  
  
10. <span data-ttu-id="557e7-126">若要實作此服務的邏輯，請在名為 StringLibrary 的專案中建立新的類別。</span><span class="sxs-lookup"><span data-stu-id="557e7-126">To implement the logic for the service, create a new class in the project called StringLibrary.</span></span>  <span data-ttu-id="557e7-127">將此類別定義替換成下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="557e7-127">Replace the class definition with the following code.</span></span>  
  
    ```  
    public class StringLibrary  
        {  
            public static String ReverseString(string StringToReverse)  
            {  
                char[] charArray = StringToReverse.ToCharArray();  
                Array.Reverse(charArray);  
                return new String(charArray);  
            }  
        }  
    ```  
  
11. <span data-ttu-id="557e7-128">若要呼叫輸入上的 ReverseString 方法，將拖曳**InvokeMethod**活動從 [工具箱] 之間的空格**接收**和**SendReply**活動。</span><span class="sxs-lookup"><span data-stu-id="557e7-128">To call the ReverseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="557e7-129">將活動的屬性設定如下：</span><span class="sxs-lookup"><span data-stu-id="557e7-129">Set the properties of the activity as follows:</span></span>  
  
    1.  <span data-ttu-id="557e7-130">**MethodName**: ReverseString</span><span class="sxs-lookup"><span data-stu-id="557e7-130">**MethodName**: ReverseString</span></span>  
  
    2.  <span data-ttu-id="557e7-131">**結果**: ReversedStringToReturn</span><span class="sxs-lookup"><span data-stu-id="557e7-131">**Result**: ReversedStringToReturn</span></span>  
  
    3.  <span data-ttu-id="557e7-132">**參數**： 建立新的參數與**方向**為 In，**類型**的字串，與**值**為 StringToReverse。</span><span class="sxs-lookup"><span data-stu-id="557e7-132">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToReverse.</span></span>  
  
    4.  <span data-ttu-id="557e7-133">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="557e7-133">**TargetType**: NestedServices.StringLibrary</span></span>  
  
12. <span data-ttu-id="557e7-134">按 F5 測試服務。</span><span class="sxs-lookup"><span data-stu-id="557e7-134">Test the service by pressing F5.</span></span> <span data-ttu-id="557e7-135">在出現的 WCF 測試用戶端中，按兩下 ReverseString() 方法。</span><span class="sxs-lookup"><span data-stu-id="557e7-135">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="557e7-136">在要求窗格中，輸入`Sample`，針對 InputString 參數的值。</span><span class="sxs-lookup"><span data-stu-id="557e7-136">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="557e7-137">按一下**叫用**。</span><span class="sxs-lookup"><span data-stu-id="557e7-137">Click **Invoke**.</span></span> <span data-ttu-id="557e7-138">此服務應該會傳回 "elpmaS"。</span><span class="sxs-lookup"><span data-stu-id="557e7-138">The service should return "elpmaS".</span></span>  
  
### <a name="to-create-the-uppercaser-workflow-service"></a><span data-ttu-id="557e7-139">若要建立 UpperCaser 工作流程服務</span><span class="sxs-lookup"><span data-stu-id="557e7-139">To create the UpperCaser workflow service</span></span>  
  
1.  <span data-ttu-id="557e7-140">以滑鼠右鍵按一下 NestedServices 專案，然後選取**新增**，**新項目**。</span><span class="sxs-lookup"><span data-stu-id="557e7-140">Right-click the NestedServices project and select **Add**, **New Item**.</span></span> <span data-ttu-id="557e7-141">在**工作流程**節點中，選取**WCF Workflow Service**，並為新的服務名稱`UpperCaserService`。</span><span class="sxs-lookup"><span data-stu-id="557e7-141">In the **Workflow** node, select **WCF Workflow Service**, and name the new service `UpperCaserService`.</span></span> <span data-ttu-id="557e7-142">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="557e7-142">Click **Add**.</span></span> <span data-ttu-id="557e7-143">這樣應該會將名為 UpperCaserService.xamlx 的新工作流程服務加入至專案中。</span><span class="sxs-lookup"><span data-stu-id="557e7-143">This should add a new workflow service called UpperCaserService.xamlx to the project.</span></span>  
  
2.  <span data-ttu-id="557e7-144">在設計工具中開啟 UpperCaserService.xamlx 並刪除現有**ReceiveRequest**和`SendReply`活動，然後拖曳`ReceiveAndSendReply`到現有的序列活動的活動。</span><span class="sxs-lookup"><span data-stu-id="557e7-144">Open UpperCaserService.xamlx in the designer and delete the existing **ReceiveRequest** and `SendReply` activities, and drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>  
  
    1.  <span data-ttu-id="557e7-145">設定**OperationName**為 UpperCaseString。</span><span class="sxs-lookup"><span data-stu-id="557e7-145">Set the **OperationName** to UpperCaseString.</span></span>  
  
    2.  <span data-ttu-id="557e7-146">設定**ServiceContractName**  設定為 IUpperCaseString。</span><span class="sxs-lookup"><span data-stu-id="557e7-146">Set the **ServiceContractName** to IUpperCaseString.</span></span>  
  
    3.  <span data-ttu-id="557e7-147">選取**CanCreateInstance**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="557e7-147">Select the **CanCreateInstance** check box.</span></span>  
  
3.  <span data-ttu-id="557e7-148">選取 [sequentialservice] 活動，然後再按一下**變數**設計工具底部的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="557e7-148">Select the SequentialService activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="557e7-149">建立三個新的變數，其名稱分別是 String 型別的 StringToUpper、StringToReverse 和 StringToReturn。</span><span class="sxs-lookup"><span data-stu-id="557e7-149">Create three new variables named StringToUpper, StringToReverse, and StringToReturn of type String.</span></span>  
  
4.  <span data-ttu-id="557e7-150">按一下**定義**中連結**接收**活動。</span><span class="sxs-lookup"><span data-stu-id="557e7-150">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="557e7-151">按一下**參數**，並建立名為 InputString 指派給 StringToUpper String 型別參數。</span><span class="sxs-lookup"><span data-stu-id="557e7-151">Click the **Parameters**, and create a parameter named InputString of type String that assigns to StringToUpper.</span></span>  
  
5.  <span data-ttu-id="557e7-152">按一下**定義**中連結**SendReplyToReceive**活動。</span><span class="sxs-lookup"><span data-stu-id="557e7-152">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="557e7-153">按一下**參數**，並建立名為 ModifiedString String 型別，指派給 StringToReturn 參數。</span><span class="sxs-lookup"><span data-stu-id="557e7-153">Click the **Parameters**, and create a parameter named ModifiedString of type String, assigned to StringToReturn.</span></span>  
  
6.  <span data-ttu-id="557e7-154">若要實作此服務的邏輯，請使用下列程式碼在 StringLibrary 類別中建立新的方法。</span><span class="sxs-lookup"><span data-stu-id="557e7-154">To implement the logic for the service, create a new method in the StringLibrary class using the following code.</span></span>  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
    ```  
  
7.  <span data-ttu-id="557e7-155">若要呼叫輸入上的 UpperCaseString 方法，將拖曳**InvokeMethod**活動從 [工具箱] 之間的空格**接收**和**SendReply**活動。</span><span class="sxs-lookup"><span data-stu-id="557e7-155">To call the UpperCaseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="557e7-156">將活動的屬性設定如下：</span><span class="sxs-lookup"><span data-stu-id="557e7-156">Set the properties of the activity as follows:</span></span>  
  
    1.  <span data-ttu-id="557e7-157">**MethodName**: UpperCaseString</span><span class="sxs-lookup"><span data-stu-id="557e7-157">**MethodName**: UpperCaseString</span></span>  
  
    2.  <span data-ttu-id="557e7-158">**結果**: StringToReverse</span><span class="sxs-lookup"><span data-stu-id="557e7-158">**Result**: StringToReverse</span></span>  
  
    3.  <span data-ttu-id="557e7-159">**參數**： 建立新的參數與**方向**為 In，**類型**的字串，與**值**為 StringToUpper。</span><span class="sxs-lookup"><span data-stu-id="557e7-159">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToUpper.</span></span>  
  
    4.  <span data-ttu-id="557e7-160">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="557e7-160">**TargetType**: NestedServices.StringLibrary</span></span>  
  
8.  <span data-ttu-id="557e7-161">現在我們要針對修改的字串呼叫第一個服務。</span><span class="sxs-lookup"><span data-stu-id="557e7-161">We’ll now call the first service on the modified string.</span></span> <span data-ttu-id="557e7-162">以滑鼠右鍵按一下專案，然後選取**加入服務參考**。</span><span class="sxs-lookup"><span data-stu-id="557e7-162">Right-click the project and select **Add Service Reference**.</span></span> <span data-ttu-id="557e7-163">加入在服務的服務參考http://localhost/NestedServices/StringReverserService.xamlx和建置專案來建立自訂的活動，以便存取第一個 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="557e7-163">Add a service reference to the service at http://localhost/NestedServices/StringReverserService.xamlx and build the project to create a custom activity to access the first Web service.</span></span>  
  
9. <span data-ttu-id="557e7-164">之間拖曳到工作流程的新活動的執行個體**InvokeMethod**活動和**SendReplyToReceive**活動。</span><span class="sxs-lookup"><span data-stu-id="557e7-164">Drag an instance of the new activity onto the workflow, between the **InvokeMethod** activity and the **SendReplyToReceive** activities.</span></span> <span data-ttu-id="557e7-165">將 StringToReverse 變數指派給新活動的 InputString 屬性，並將 StringToReturn 變數指派給 StringToReturn 屬性。</span><span class="sxs-lookup"><span data-stu-id="557e7-165">Assign the variable StringToReverse to the InputString property of the new activity, and the variable StringToReturn to the StringToReturn property.</span></span>  
  
10. <span data-ttu-id="557e7-166">開啟 NestedServices 專案的 屬性 頁面並變更**特定頁面**中**Web**為 UpperCaserService.xamlx 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="557e7-166">Open the Properties page for the NestedServices project, and change the **Specific Page** in the **Web** tab to UpperCaserService.xamlx.</span></span>  
  
11. <span data-ttu-id="557e7-167">按 F5 測試服務。</span><span class="sxs-lookup"><span data-stu-id="557e7-167">Test the service by pressing F5.</span></span> <span data-ttu-id="557e7-168">在出現的 WCF 測試用戶端中，按兩下 ReverseString() 方法。</span><span class="sxs-lookup"><span data-stu-id="557e7-168">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="557e7-169">在要求窗格中，輸入`Sample`，針對 InputString 參數的值。</span><span class="sxs-lookup"><span data-stu-id="557e7-169">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="557e7-170">按一下**叫用**。</span><span class="sxs-lookup"><span data-stu-id="557e7-170">Click **Invoke**.</span></span> <span data-ttu-id="557e7-171">此服務應該會傳回 "ELPMAS"。</span><span class="sxs-lookup"><span data-stu-id="557e7-171">The service should return "ELPMAS".</span></span>  
  
### <a name="to-create-a-client-to-call-the-services"></a><span data-ttu-id="557e7-172">若要建立用戶端來呼叫服務</span><span class="sxs-lookup"><span data-stu-id="557e7-172">To create a client to call the services</span></span>  
  
1.  <span data-ttu-id="557e7-173">將名為 Client 的新主控台應用程式專案加入至方案中。</span><span class="sxs-lookup"><span data-stu-id="557e7-173">Add a new Console application project called Client to the solution.</span></span>  
  
2.  <span data-ttu-id="557e7-174">以滑鼠右鍵按一下 用戶端專案，然後選取**加入服務參考**。</span><span class="sxs-lookup"><span data-stu-id="557e7-174">Right-click the Client project and select **Add Service Reference**.</span></span> <span data-ttu-id="557e7-175">在出現的視窗中，按一下**探索**。</span><span class="sxs-lookup"><span data-stu-id="557e7-175">In the window that appears, click **Discover**.</span></span> <span data-ttu-id="557e7-176">選取 StringReverserService.xamlx 並輸入 ReverseService 當做命名空間。</span><span class="sxs-lookup"><span data-stu-id="557e7-176">Select StringReverserService.xamlx, and enter ReverseService as the namespace.</span></span>  <span data-ttu-id="557e7-177">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="557e7-177">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="557e7-178">用下列程式碼取代 Program.cs 中的 Main 方法。</span><span class="sxs-lookup"><span data-stu-id="557e7-178">Replace the Main method in Program.cs with the following code.</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
        Console.Write("Input string to process:");  
        String input = Console.ReadLine();  
        var service = new ReverseService.ReverseStringClient();  
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));  
        Console.ReadKey();  
    }  
    ```
