---
title: HOW TO：加入資料服務參考（WCF Data Services）
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790746"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="76fc3-102">作法：加入資料服務參考（WCF Data Services）</span><span class="sxs-lookup"><span data-stu-id="76fc3-102">How to: Add a data service reference (WCF Data Services)</span></span>

<span data-ttu-id="76fc3-103">您可以使用 Visual Studio 中的 [**加入服務參考**] 對話方塊，將參考新增至 WCF Data Services。</span><span class="sxs-lookup"><span data-stu-id="76fc3-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="76fc3-104">這樣可以讓您更輕鬆地在 Visual Studio 開發的用戶端應用程式中存取資料服務。</span><span class="sxs-lookup"><span data-stu-id="76fc3-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="76fc3-105">當您完成此程序時，會根據從資料服務取得的中繼資料產生資料類別。</span><span class="sxs-lookup"><span data-stu-id="76fc3-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="76fc3-106">如需詳細資訊，請參閱[產生資料服務用戶端程式庫](generating-the-data-service-client-library-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="76fc3-106">For more information, see [Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="76fc3-107">加入資料服務參考</span><span class="sxs-lookup"><span data-stu-id="76fc3-107">Add a data service reference</span></span>

1. <span data-ttu-id="76fc3-108">(選擇性) 如果資料服務不是方案的一部分且尚未執行，請啟動資料服務，並且記下資料服務的 URI。</span><span class="sxs-lookup"><span data-stu-id="76fc3-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="76fc3-109">在 Visual Studio 的**方案總管**中，以滑鼠右鍵按一下用戶端專案，然後選取 [**加入** > **服務參考**]。</span><span class="sxs-lookup"><span data-stu-id="76fc3-109">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="76fc3-110">如果資料服務是目前方案的一部分，請按一下 [**探索**]。</span><span class="sxs-lookup"><span data-stu-id="76fc3-110">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="76fc3-111">-或-</span><span class="sxs-lookup"><span data-stu-id="76fc3-111">-or-</span></span>

     <span data-ttu-id="76fc3-112">在 [**位址**] 文字方塊中，輸入資料服務的基底 URL，例如`http://localhost:1234/Northwind.svc`，然後按一下 [**移至**]。</span><span class="sxs-lookup"><span data-stu-id="76fc3-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="76fc3-113">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="76fc3-113">Select **OK**.</span></span>

     <span data-ttu-id="76fc3-114">新的程式碼檔案，其中包含可存取資料服務資源並與之互動的資料類別，會加入至專案。</span><span class="sxs-lookup"><span data-stu-id="76fc3-114">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="76fc3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76fc3-115">See also</span></span>

- [<span data-ttu-id="76fc3-116">快速入門</span><span class="sxs-lookup"><span data-stu-id="76fc3-116">Quickstart</span></span>](quickstart-wcf-data-services.md)
