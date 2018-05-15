---
title: 模型定義函式
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 5c91c221735f3385370ec2fbb532d5b3c5dd2898
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="model-defined-function"></a><span data-ttu-id="cfd9c-102">模型定義函式</span><span class="sxs-lookup"><span data-stu-id="cfd9c-102">model-defined function</span></span>
<span data-ttu-id="cfd9c-103">A*模型定義函式*是概念模型中所定義的函式。</span><span class="sxs-lookup"><span data-stu-id="cfd9c-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="cfd9c-104">模型定義函式的主體以表示[Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)、 表示之外，獨立函式可讓規則或資料來源中支援的語言。</span><span class="sxs-lookup"><span data-stu-id="cfd9c-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="cfd9c-105">模型定義函式的定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="cfd9c-105">A definition for a model-defined function contains the following information:</span></span>  
  
-   <span data-ttu-id="cfd9c-106">函式名稱。</span><span class="sxs-lookup"><span data-stu-id="cfd9c-106">A function name.</span></span> <span data-ttu-id="cfd9c-107">(必要項)</span><span class="sxs-lookup"><span data-stu-id="cfd9c-107">(Required)</span></span>  
  
-   <span data-ttu-id="cfd9c-108">傳回值的型別。</span><span class="sxs-lookup"><span data-stu-id="cfd9c-108">The type of the return value.</span></span> <span data-ttu-id="cfd9c-109">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="cfd9c-109">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cfd9c-110">若未指定任何傳回型別，則傳回值為 void。</span><span class="sxs-lookup"><span data-stu-id="cfd9c-110">If no return type is specified, the return value is void.</span></span>  
  
-   <span data-ttu-id="cfd9c-111">參數資訊。</span><span class="sxs-lookup"><span data-stu-id="cfd9c-111">Parameter information.</span></span> <span data-ttu-id="cfd9c-112">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="cfd9c-112">(Optional)</span></span>  
  
-   <span data-ttu-id="cfd9c-113">[Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)定義函式主體的運算式。</span><span class="sxs-lookup"><span data-stu-id="cfd9c-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="cfd9c-114">請注意，模型定義函式不支援輸出參數。</span><span class="sxs-lookup"><span data-stu-id="cfd9c-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="cfd9c-115">有此限制後才能夠撰寫模型定義函式。</span><span class="sxs-lookup"><span data-stu-id="cfd9c-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfd9c-116">範例</span><span class="sxs-lookup"><span data-stu-id="cfd9c-116">Example</span></span>  
 <span data-ttu-id="cfd9c-117">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="cfd9c-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="cfd9c-118">![具有發行日期的模型](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span><span class="sxs-lookup"><span data-stu-id="cfd9c-118">![Model With Published Date](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span></span>  
  
 <span data-ttu-id="cfd9c-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="cfd9c-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="cfd9c-120">下列 CSDL 定義概念模型中的函式，會傳回上圖中 `Book` 執行個體發行年度以來的年份。</span><span class="sxs-lookup"><span data-stu-id="cfd9c-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="cfd9c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfd9c-121">See Also</span></span>  
 [<span data-ttu-id="cfd9c-122">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="cfd9c-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="cfd9c-123">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="cfd9c-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="cfd9c-124">實體資料模型：基本資料類型</span><span class="sxs-lookup"><span data-stu-id="cfd9c-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
