---
title: "HOW TO：建立會取用現有服務合約的工作流程服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb58664b57261eb09886ec0e8f97fcdbe45cdd4f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="9fbf4-102">HOW TO：建立會取用現有服務合約的工作流程服務</span><span class="sxs-lookup"><span data-stu-id="9fbf4-102">How to: Create a workflow service that consumes an existing service contract</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="9fbf4-103"> 採用合約優先工作流程開發形式，可在 Web 服務和工作流程中提供更好的整合。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-103"> features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="9fbf4-104">合約優先工作流程開發工具可讓您在 Code First 中設計合約。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="9fbf4-105">此工具會自動在合約中的作業工具箱內產生活動範本。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fbf4-106">本主題提供建立合約優先工作流程服務的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9fbf4-107">合約優先工作流程服務開發，請參閱[合約第一個工作流程服務開發](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md)。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-107"> contract-first workflow service development, see [Contract First Workflow Service Development](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="9fbf4-108">建立工作流程專案</span><span class="sxs-lookup"><span data-stu-id="9fbf4-108">Creating the workflow project</span></span>  
  
1.  <span data-ttu-id="9fbf4-109">在[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]，選取**檔案**，**新專案**。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-109">In [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], select **File**, **New Project**.</span></span> <span data-ttu-id="9fbf4-110">選取**WCF**節點下的**C#**節點**範本**樹狀，並選取**WCF 工作流程服務應用程式**範本。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2.  <span data-ttu-id="9fbf4-111">將新專案`ContractFirst`按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="9fbf4-112">建立服務合約</span><span class="sxs-lookup"><span data-stu-id="9fbf4-112">Creating the service contract</span></span>  
  
1.  <span data-ttu-id="9fbf4-113">中的專案上按一下滑鼠右鍵**方案總管 中**選取**新增**，**新項目...**.</span><span class="sxs-lookup"><span data-stu-id="9fbf4-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="9fbf4-114">選取**程式碼**節點的左側，而**類別**右邊的範本。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="9fbf4-115">將新類別`IBookService`按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2.  <span data-ttu-id="9fbf4-116">在出現的程式碼視窗最上方，將 Using 陳述式加入到 `System.Servicemodel`。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  <span data-ttu-id="9fbf4-117">將範例類別定義變更為下列介面定義。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  <span data-ttu-id="9fbf4-118">建置專案時按**Ctrl + Shift + B**。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="9fbf4-119">匯入服務合約</span><span class="sxs-lookup"><span data-stu-id="9fbf4-119">Importing the service contract</span></span>  
  
1.  <span data-ttu-id="9fbf4-120">中的專案上按一下滑鼠右鍵**方案總管 中**選取**匯入服務合約**。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="9fbf4-121">在下**\<目前專案 >**，開啟所有的子節點並選取**IBookService**。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="9fbf4-122">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-122">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="9fbf4-123">隨即會開啟一個對話方塊，警告您作業已成功完成，且所產生的活動將會在您建置專案後出現在工具箱中。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="9fbf4-124">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-124">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="9fbf4-125">建置專案時按**Ctrl + Shift + B**，如此一來，匯入的活動將會出現在工具箱中。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4.  <span data-ttu-id="9fbf4-126">在**方案總管 中**，開啟.service1.xamlx。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="9fbf4-127">工作流程服務會出現在設計工具中。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-127">The workflow service will appear in the designer.</span></span>  
  
5.  <span data-ttu-id="9fbf4-128">選取**順序**活動。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="9fbf4-129">在 [屬性] 視窗中，按一下**...**</span><span class="sxs-lookup"><span data-stu-id="9fbf4-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="9fbf4-130">按鈕**ImplementedContract**屬性。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="9fbf4-131">在**型別集合編輯器**視窗中，按一下 **類型**下拉式清單中，然後選取**瀏覽型別...**</span><span class="sxs-lookup"><span data-stu-id="9fbf4-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="9fbf4-132">項目。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-132">entry.</span></span> <span data-ttu-id="9fbf4-133">在**瀏覽並選取.Net 型別**對話方塊下方**\<目前專案 >**，開啟所有的子節點並選取**IBookService**。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-133">In the **Browse and Select a .Net Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="9fbf4-134">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-134">Click **OK**.</span></span> <span data-ttu-id="9fbf4-135">在**型別集合編輯器**] 對話方塊中，按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6.  <span data-ttu-id="9fbf4-136">選取並刪除**ReceiveRequest**和**SendResponse**活動。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7.  <span data-ttu-id="9fbf4-137">從工具箱 拖曳**Buy_ReceiveAndSendReply**和**Checkout_Receive**活動放置到**循序服務**活動。</span><span class="sxs-lookup"><span data-stu-id="9fbf4-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
