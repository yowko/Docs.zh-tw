---
title: 作法：建立會取用現有服務合約的工作流程服務
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 05c59bde424049eb5bef8f8bd09c472b58eaa9ef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248821"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="08148-102">作法：建立會取用現有服務合約的工作流程服務</span><span class="sxs-lookup"><span data-stu-id="08148-102">How to: Create a workflow service that consumes an existing service contract</span></span>

<span data-ttu-id="08148-103">.NET Framework 4.5 以合約優先工作流程開發的形式，在 web 服務與工作流程之間提供更好的整合。</span><span class="sxs-lookup"><span data-stu-id="08148-103">.NET Framework 4.5 features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="08148-104">合約優先工作流程開發工具可讓您在 Code First 中設計合約。</span><span class="sxs-lookup"><span data-stu-id="08148-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="08148-105">此工具會自動在合約中的作業工具箱內產生活動範本。</span><span class="sxs-lookup"><span data-stu-id="08148-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08148-106">本主題提供建立合約優先工作流程服務的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="08148-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="08148-107">如需有關合約優先工作流程服務開發的詳細資訊，請參閱 [合約優先工作流程服務開發](contract-first-workflow-service-development.md)。</span><span class="sxs-lookup"><span data-stu-id="08148-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="08148-108">建立工作流程專案</span><span class="sxs-lookup"><span data-stu-id="08148-108">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="08148-109">在 Visual Studio 中，選取 [檔案]、[新增專案]。</span><span class="sxs-lookup"><span data-stu-id="08148-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="08148-110">在 [**範本**] 樹狀結構中，選取 [ **c #** ] 節點底下的 [ **wcf** ] 節點，然後選取 [ **wcf Workflow Service 應用程式**] 範本。</span><span class="sxs-lookup"><span data-stu-id="08148-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="08148-111">將新專案命名為 `ContractFirst` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="08148-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="08148-112">建立服務合約</span><span class="sxs-lookup"><span data-stu-id="08148-112">Creating the service contract</span></span>  
  
1. <span data-ttu-id="08148-113">以滑鼠右鍵按一下 **方案總管** 中的專案，然後選取 [ **加入**]、[ **新增專案 ...**]。</span><span class="sxs-lookup"><span data-stu-id="08148-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="08148-114">選取左側的 [程式 **代碼** ] 節點和右邊的 [ **類別** ] 範本。</span><span class="sxs-lookup"><span data-stu-id="08148-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="08148-115">將新類別命名為 `IBookService` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="08148-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="08148-116">在出現的程式碼視窗最上方，將 Using 陳述式加入到 `System.Servicemodel`。</span><span class="sxs-lookup"><span data-stu-id="08148-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="08148-117">將範例類別定義變更為下列介面定義。</span><span class="sxs-lookup"><span data-stu-id="08148-117">Change the sample class definition to the following interface definition.</span></span>  
  
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
  
4. <span data-ttu-id="08148-118">按下 **Ctrl + Shift + B** 以建立專案。</span><span class="sxs-lookup"><span data-stu-id="08148-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="08148-119">匯入服務合約</span><span class="sxs-lookup"><span data-stu-id="08148-119">Importing the service contract</span></span>  
  
1. <span data-ttu-id="08148-120">以滑鼠右鍵按一下 **方案總管** 中的專案，然後選取 [匯 **入服務合約**]。</span><span class="sxs-lookup"><span data-stu-id="08148-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="08148-121">在底下 **\<Current Project>** ，開啟所有子節點，然後選取 [ **[ibookservice**]。</span><span class="sxs-lookup"><span data-stu-id="08148-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="08148-122">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="08148-122">Click **OK**.</span></span>  
  
2. <span data-ttu-id="08148-123">隨即會開啟一個對話方塊，警告您作業已成功完成，且所產生的活動將會在您建置專案後出現在工具箱中。</span><span class="sxs-lookup"><span data-stu-id="08148-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="08148-124">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="08148-124">Click **OK**.</span></span>  
  
3. <span data-ttu-id="08148-125">按 **Ctrl + Shift + B** 來建立專案，讓匯入的活動會出現在 [工具箱] 中。</span><span class="sxs-lookup"><span data-stu-id="08148-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="08148-126">在 **方案總管** 中，開啟 Service1 service1.xamlx。</span><span class="sxs-lookup"><span data-stu-id="08148-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="08148-127">工作流程服務會出現在設計工具中。</span><span class="sxs-lookup"><span data-stu-id="08148-127">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="08148-128">選取 **序列** 活動。</span><span class="sxs-lookup"><span data-stu-id="08148-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="08148-129">在 [屬性視窗中，按一下 **...**</span><span class="sxs-lookup"><span data-stu-id="08148-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="08148-130">按鈕（ **ImplementedContract** 屬性）。</span><span class="sxs-lookup"><span data-stu-id="08148-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="08148-131">在出現的 [**型別集合編輯器**] 視窗中，按一下 [**類型**] 下拉式清單，然後選取 [**流覽類型 ...]** 。</span><span class="sxs-lookup"><span data-stu-id="08148-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="08148-132">項目。</span><span class="sxs-lookup"><span data-stu-id="08148-132">entry.</span></span> <span data-ttu-id="08148-133">在 [ **流覽並選取 .Net 類型** ] 對話方塊中，于底下 **\<Current Project>** 開啟 [所有子節點]，然後選取 [ **[ibookservice**]。</span><span class="sxs-lookup"><span data-stu-id="08148-133">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="08148-134">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="08148-134">Click **OK**.</span></span> <span data-ttu-id="08148-135">在 [ **型別集合編輯器** ] 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="08148-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="08148-136">選取並刪除 **ReceiveRequest** 和 **SendResponse** 活動。</span><span class="sxs-lookup"><span data-stu-id="08148-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="08148-137">將 [ **Buy_ReceiveAndSendReply** ] 和 [ **Checkout_Receive** ] 活動從 [工具箱] 拖曳到 [ **順序服務** ] 活動上。</span><span class="sxs-lookup"><span data-stu-id="08148-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
