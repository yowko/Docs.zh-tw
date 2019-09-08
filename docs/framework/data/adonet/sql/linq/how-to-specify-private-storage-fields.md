---
title: 作法：指定私用儲存欄位
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: e6e6a4e28fbfb327f25874844f28bcbafa6d2805
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793211"
---
# <a name="how-to-specify-private-storage-fields"></a><span data-ttu-id="20007-102">作法：指定私用儲存欄位</span><span class="sxs-lookup"><span data-stu-id="20007-102">How to: Specify Private Storage Fields</span></span>
<span data-ttu-id="20007-103">使用屬性（ <xref:System.Data.Linq.Mapping.DataAttribute> attribute）上的屬性（property）來指定基礎儲存欄位的名稱。<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20007-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property on the <xref:System.Data.Linq.Mapping.DataAttribute> attribute to designate the name of an underlying storage field.</span></span>  
  
 <span data-ttu-id="20007-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>。</span><span class="sxs-lookup"><span data-stu-id="20007-104">For code examples, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a><span data-ttu-id="20007-105">若要指定基礎儲存欄位的名稱</span><span class="sxs-lookup"><span data-stu-id="20007-105">To specify the name of an underlying storage field</span></span>  
  
1. <span data-ttu-id="20007-106">將 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="20007-106">Add the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="20007-107">指定欄位名稱做為 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 屬性 (Property) 的值。</span><span class="sxs-lookup"><span data-stu-id="20007-107">Assign the name of the field as the value of the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20007-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20007-108">See also</span></span>

- [<span data-ttu-id="20007-109">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="20007-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="20007-110">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="20007-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
