---
title: 模型定義函式
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 1418eccecea647204620455969696c6390bd4a18
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783613"
---
# <a name="model-defined-function"></a><span data-ttu-id="da68b-102">模型定義函式</span><span class="sxs-lookup"><span data-stu-id="da68b-102">model-defined function</span></span>
<span data-ttu-id="da68b-103">*模型定義函式*是在概念模型中定義的函數。</span><span class="sxs-lookup"><span data-stu-id="da68b-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="da68b-104">模型定義函式的主體會以[Entity SQL](./ef/language-reference/entity-sql-language.md)表示，讓函數可以獨立于資料來源中支援的規則或語言來表示。</span><span class="sxs-lookup"><span data-stu-id="da68b-104">The body of a model-defined function is expressed in [Entity SQL](./ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="da68b-105">模型定義函式的定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="da68b-105">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="da68b-106">函式名稱。</span><span class="sxs-lookup"><span data-stu-id="da68b-106">A function name.</span></span> <span data-ttu-id="da68b-107">(必要項)</span><span class="sxs-lookup"><span data-stu-id="da68b-107">(Required)</span></span>  
  
- <span data-ttu-id="da68b-108">傳回值的型別。</span><span class="sxs-lookup"><span data-stu-id="da68b-108">The type of the return value.</span></span> <span data-ttu-id="da68b-109">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="da68b-109">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="da68b-110">若未指定任何傳回型別，則傳回值為 void。</span><span class="sxs-lookup"><span data-stu-id="da68b-110">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="da68b-111">參數資訊。</span><span class="sxs-lookup"><span data-stu-id="da68b-111">Parameter information.</span></span> <span data-ttu-id="da68b-112">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="da68b-112">(Optional)</span></span>  
  
- <span data-ttu-id="da68b-113">定義函數主體的[Entity SQL](./ef/language-reference/entity-sql-language.md)運算式。</span><span class="sxs-lookup"><span data-stu-id="da68b-113">An [Entity SQL](./ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="da68b-114">請注意，模型定義函式不支援輸出參數。</span><span class="sxs-lookup"><span data-stu-id="da68b-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="da68b-115">有此限制後才能夠撰寫模型定義函式。</span><span class="sxs-lookup"><span data-stu-id="da68b-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da68b-116">範例</span><span class="sxs-lookup"><span data-stu-id="da68b-116">Example</span></span>  
 <span data-ttu-id="da68b-117">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="da68b-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![顯示具有發行日期之模型的螢幕擷取畫面。](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="da68b-119">[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的特定領域語言（DSL）來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="da68b-119">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="da68b-120">下列 CSDL 定義概念模型中的函式，會傳回上圖中 `Book` 執行個體發行年度以來的年份。</span><span class="sxs-lookup"><span data-stu-id="da68b-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="da68b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da68b-121">See also</span></span>

- [<span data-ttu-id="da68b-122">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="da68b-122">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="da68b-123">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="da68b-123">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="da68b-124">實體資料模型：基本資料類型</span><span class="sxs-lookup"><span data-stu-id="da68b-124">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)
