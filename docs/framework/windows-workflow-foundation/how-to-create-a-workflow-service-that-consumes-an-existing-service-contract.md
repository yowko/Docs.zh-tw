---
title: 作法：建立會取用現有服務合約的工作流程服務
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 6d7fa8c9faa84efc84243387cd27aa264f6155eb
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989616"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="92f35-102">作法：建立會取用現有服務合約的工作流程服務</span><span class="sxs-lookup"><span data-stu-id="92f35-102">How to: Create a workflow service that consumes an existing service contract</span></span>
<span data-ttu-id="92f35-103">.NET Framework 4.5 以合約優先工作流程開發形式，在 web 服務與工作流程之間提供更好的整合。</span><span class="sxs-lookup"><span data-stu-id="92f35-103">.NET Framework 4.5 features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="92f35-104">合約優先工作流程開發工具可讓您在 Code First 中設計合約。</span><span class="sxs-lookup"><span data-stu-id="92f35-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="92f35-105">此工具會自動在合約中的作業工具箱內產生活動範本。</span><span class="sxs-lookup"><span data-stu-id="92f35-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92f35-106">本主題提供建立合約優先工作流程服務的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="92f35-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="92f35-107">如需有關合約優先工作流程服務開發的詳細資訊，請參閱[合約優先工作流程服務開發](contract-first-workflow-service-development.md)。</span><span class="sxs-lookup"><span data-stu-id="92f35-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="92f35-108">建立工作流程專案</span><span class="sxs-lookup"><span data-stu-id="92f35-108">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="92f35-109">在 Visual Studio 中，**選取 [** 檔案]、[**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="92f35-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="92f35-110">在 [**範本**] 樹狀結構**C#** 中，選取節點底下的 [ **wcf** ] 節點，然後選取 [ **wcf 工作流程服務應用程式**] 範本。</span><span class="sxs-lookup"><span data-stu-id="92f35-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="92f35-111">將新專案`ContractFirst`命名為，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="92f35-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="92f35-112">建立服務合約</span><span class="sxs-lookup"><span data-stu-id="92f35-112">Creating the service contract</span></span>  
  
1. <span data-ttu-id="92f35-113">以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [**加入**]、[**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="92f35-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="92f35-114">選取左側的 [程式**代碼**] 節點，以及右側的 [**類別**] 範本。</span><span class="sxs-lookup"><span data-stu-id="92f35-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="92f35-115">將新類別`IBookService`命名為，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="92f35-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="92f35-116">在出現的程式碼視窗最上方，將 Using 陳述式加入到 `System.Servicemodel`。</span><span class="sxs-lookup"><span data-stu-id="92f35-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="92f35-117">將範例類別定義變更為下列介面定義。</span><span class="sxs-lookup"><span data-stu-id="92f35-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. <span data-ttu-id="92f35-118">按**Ctrl + Shift + B**來建立專案。</span><span class="sxs-lookup"><span data-stu-id="92f35-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="92f35-119">匯入服務合約</span><span class="sxs-lookup"><span data-stu-id="92f35-119">Importing the service contract</span></span>  
  
1. <span data-ttu-id="92f35-120">以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [匯**入服務合約**]。</span><span class="sxs-lookup"><span data-stu-id="92f35-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="92f35-121">底下 **\<目前專案>** 開啟 所有子節點，然後選取 **IBookService**。</span><span class="sxs-lookup"><span data-stu-id="92f35-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="92f35-122">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="92f35-122">Click **OK**.</span></span>  
  
2. <span data-ttu-id="92f35-123">隨即會開啟一個對話方塊，警告您作業已成功完成，且所產生的活動將會在您建置專案後出現在工具箱中。</span><span class="sxs-lookup"><span data-stu-id="92f35-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="92f35-124">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="92f35-124">Click **OK**.</span></span>  
  
3. <span data-ttu-id="92f35-125">按**Ctrl + Shift + B**來建立專案，匯入的活動就會出現在 [工具箱] 中。</span><span class="sxs-lookup"><span data-stu-id="92f35-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="92f35-126">在**方案總管**中，開啟 Service1 service1.xamlx。</span><span class="sxs-lookup"><span data-stu-id="92f35-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="92f35-127">工作流程服務會出現在設計工具中。</span><span class="sxs-lookup"><span data-stu-id="92f35-127">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="92f35-128">選取 [**序列**] 活動。</span><span class="sxs-lookup"><span data-stu-id="92f35-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="92f35-129">在 屬性視窗中，按一下  **...**</span><span class="sxs-lookup"><span data-stu-id="92f35-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="92f35-130">**ImplementedContract**屬性中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="92f35-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="92f35-131">在出現的 [**類型集合編輯器**] 視窗中，按一下 [**類型**] 下拉式清單，然後選取 [**流覽類型]** 。</span><span class="sxs-lookup"><span data-stu-id="92f35-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="92f35-132">上場.</span><span class="sxs-lookup"><span data-stu-id="92f35-132">entry.</span></span> <span data-ttu-id="92f35-133">在 **瀏覽並選取.NET 型別** 對話方塊底下 **\<目前專案>** 開啟所有子節點，然後選取 **IBookService**。</span><span class="sxs-lookup"><span data-stu-id="92f35-133">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="92f35-134">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="92f35-134">Click **OK**.</span></span> <span data-ttu-id="92f35-135">在 [**類型集合編輯器**] 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="92f35-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="92f35-136">選取並刪除**ReceiveRequest**和**SendResponse**活動。</span><span class="sxs-lookup"><span data-stu-id="92f35-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="92f35-137">將**Buy_ReceiveAndSendReply**和**Checkout_Receive**活動從 [工具箱] 拖曳至 [**順序服務**] 活動。</span><span class="sxs-lookup"><span data-stu-id="92f35-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
