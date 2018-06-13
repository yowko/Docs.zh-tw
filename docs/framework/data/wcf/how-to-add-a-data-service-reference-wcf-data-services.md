---
title: 如何：加入資料服務參考 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: a8dcc01fb7a564a363cabed6a22738cd520d317f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356227"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="8f2e1-102">如何：加入資料服務參考 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="8f2e1-102">How to: Add a Data Service Reference (WCF Data Services)</span></span>
<span data-ttu-id="8f2e1-103">您可以使用**加入服務參考**將參考加入至 Visual Studio 中的對話方塊[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8f2e1-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span> <span data-ttu-id="8f2e1-104">這樣可以讓您更輕鬆地在 Visual Studio 開發的用戶端應用程式中存取資料服務。</span><span class="sxs-lookup"><span data-stu-id="8f2e1-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="8f2e1-105">當您完成此程序時，會根據從資料服務取得的中繼資料產生資料類別。</span><span class="sxs-lookup"><span data-stu-id="8f2e1-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="8f2e1-106">如需詳細資訊，請參閱[產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8f2e1-106">For more information, see [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span></span>  
  
### <a name="to-add-a-data-service-reference"></a><span data-ttu-id="8f2e1-107">加入資料服務參考</span><span class="sxs-lookup"><span data-stu-id="8f2e1-107">To add a data service reference</span></span>  
  
1.  <span data-ttu-id="8f2e1-108">(選擇性) 如果資料服務不是方案的一部分且尚未執行，請啟動資料服務，並且記下資料服務的 URI。</span><span class="sxs-lookup"><span data-stu-id="8f2e1-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>  
  
2.  <span data-ttu-id="8f2e1-109">以滑鼠右鍵按一下 用戶端專案，然後選取**加入服務參考**。</span><span class="sxs-lookup"><span data-stu-id="8f2e1-109">Right-click the client project and then select **Add Service Reference**.</span></span>  
  
3.  <span data-ttu-id="8f2e1-110">如果資料服務目前方案的一部分，請按一下**探索**。</span><span class="sxs-lookup"><span data-stu-id="8f2e1-110">If the data service is part of the current solution, click **Discover**.</span></span>  
  
     <span data-ttu-id="8f2e1-111">-或-</span><span class="sxs-lookup"><span data-stu-id="8f2e1-111">-or-</span></span>  
  
     <span data-ttu-id="8f2e1-112">在**位址**文字方塊中，輸入基底 URL 的資料服務，例如`http://localhost:1234/Northwind.svc`，然後按一下 **移**。</span><span class="sxs-lookup"><span data-stu-id="8f2e1-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>  
  
4.  <span data-ttu-id="8f2e1-113">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="8f2e1-113">Click **OK**.</span></span>  
  
     <span data-ttu-id="8f2e1-114">這將會加入包含資料類別的新程式碼檔案，可用於存取資料服務資源物件，並與其進行互動。</span><span class="sxs-lookup"><span data-stu-id="8f2e1-114">This adds a new code file that contains the data classes that are used to access and interact with data service resources as objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f2e1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f2e1-115">See Also</span></span>  
 [<span data-ttu-id="8f2e1-116">快速入門</span><span class="sxs-lookup"><span data-stu-id="8f2e1-116">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
