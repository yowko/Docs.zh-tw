---
title: "模型宣告函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 37c6b04fbea69f62aaf7bc148ee04ace5a5a349c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="model-declared-function"></a><span data-ttu-id="5a96c-102">模型宣告函式</span><span class="sxs-lookup"><span data-stu-id="5a96c-102">model-declared function</span></span>
<span data-ttu-id="5a96c-103">A*模型宣告函式*的函式的宣告在概念模型中，但未定義該概念模型中。</span><span class="sxs-lookup"><span data-stu-id="5a96c-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="5a96c-104">該函式可能是在裝載或儲存環境中定義的。</span><span class="sxs-lookup"><span data-stu-id="5a96c-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="5a96c-105">例如，模型宣告函式可能對應到在資料庫中定義的函式，因而在概念模型中公開伺服器端的功能。</span><span class="sxs-lookup"><span data-stu-id="5a96c-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="5a96c-106">模型宣告函式的宣告包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="5a96c-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="5a96c-107">函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a96c-107">The name of the function.</span></span> <span data-ttu-id="5a96c-108">(必要項)</span><span class="sxs-lookup"><span data-stu-id="5a96c-108">(Required)</span></span>  
  
-   <span data-ttu-id="5a96c-109">傳回值的型別。</span><span class="sxs-lookup"><span data-stu-id="5a96c-109">The type of the return value.</span></span> <span data-ttu-id="5a96c-110">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="5a96c-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a96c-111">若未指定任何傳回值，則傳回型別為 void。</span><span class="sxs-lookup"><span data-stu-id="5a96c-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="5a96c-112">參數資訊，包括參數名稱和型別。</span><span class="sxs-lookup"><span data-stu-id="5a96c-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="5a96c-113">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="5a96c-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a96c-114">範例</span><span class="sxs-lookup"><span data-stu-id="5a96c-114">Example</span></span>  
 <span data-ttu-id="5a96c-115">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="5a96c-115">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="5a96c-116">在 CSDL 中，模型宣告函式的一個實作是[函式匯入](http://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d)。</span><span class="sxs-lookup"><span data-stu-id="5a96c-116">In CSDL, one implementation of a model-declared function is a [function import](http://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d).</span></span> <span data-ttu-id="5a96c-117">下列 CSDL 定義具有函式匯入定義的實體容器。</span><span class="sxs-lookup"><span data-stu-id="5a96c-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="5a96c-118">請注意，由於沒有指定傳回型別，因此該函式的傳回型別為 void。</span><span class="sxs-lookup"><span data-stu-id="5a96c-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="5a96c-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="5a96c-119">See Also</span></span>  
 [<span data-ttu-id="5a96c-120">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="5a96c-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="5a96c-121">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="5a96c-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
