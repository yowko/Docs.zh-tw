---
title: 如何：加入資料服務參考 (WCF 資料服務)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: fc1786e1c6102c702374989253cd3ce23e3f7b54
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084633"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="51d0a-102">如何： 加入資料服務參考 (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="51d0a-102">How to: Add a data service reference (WCF Data Services)</span></span>

<span data-ttu-id="51d0a-103">您可以使用**加入服務參考**對話方塊在 Visual Studio 中將參考加入至 WCF Data Services。</span><span class="sxs-lookup"><span data-stu-id="51d0a-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="51d0a-104">這樣可以讓您更輕鬆地在 Visual Studio 開發的用戶端應用程式中存取資料服務。</span><span class="sxs-lookup"><span data-stu-id="51d0a-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="51d0a-105">當您完成此程序時，會根據從資料服務取得的中繼資料產生資料類別。</span><span class="sxs-lookup"><span data-stu-id="51d0a-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="51d0a-106">如需詳細資訊，請參閱 <<c0> [ 產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="51d0a-106">For more information, see [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="51d0a-107">加入資料服務參考</span><span class="sxs-lookup"><span data-stu-id="51d0a-107">Add a data service reference</span></span>

1. <span data-ttu-id="51d0a-108">(選擇性) 如果資料服務不是方案的一部分且尚未執行，請啟動資料服務，並且記下資料服務的 URI。</span><span class="sxs-lookup"><span data-stu-id="51d0a-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="51d0a-109">在 Visual Studio 中，在**方案總管**，以滑鼠右鍵按一下 用戶端專案，然後選取**新增** > **服務參考**。</span><span class="sxs-lookup"><span data-stu-id="51d0a-109">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="51d0a-110">如果資料服務的目前方案的一部分，請按一下**探索**。</span><span class="sxs-lookup"><span data-stu-id="51d0a-110">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="51d0a-111">-或-</span><span class="sxs-lookup"><span data-stu-id="51d0a-111">-or-</span></span>

     <span data-ttu-id="51d0a-112">在 **地址**文字方塊中，輸入基底 URL 的資料服務，例如`http://localhost:1234/Northwind.svc`，然後按一下 **移**。</span><span class="sxs-lookup"><span data-stu-id="51d0a-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="51d0a-113">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="51d0a-113">Select **OK**.</span></span>

     <span data-ttu-id="51d0a-114">包含可以存取和使用資料服務資源的資料類別的新程式碼檔案會加入至專案。</span><span class="sxs-lookup"><span data-stu-id="51d0a-114">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="51d0a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51d0a-115">See also</span></span>

- [<span data-ttu-id="51d0a-116">快速入門</span><span class="sxs-lookup"><span data-stu-id="51d0a-116">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)