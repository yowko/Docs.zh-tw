---
title: HOW TO：指定私用儲存欄位
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: 843b7ae8dbddb76e0e5fa33d3594a5655dbf1a37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902716"
---
# <a name="how-to-specify-private-storage-fields"></a><span data-ttu-id="930e5-102">HOW TO：指定私用儲存欄位</span><span class="sxs-lookup"><span data-stu-id="930e5-102">How to: Specify Private Storage Fields</span></span>
<span data-ttu-id="930e5-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>屬性上的<xref:System.Data.Linq.Mapping.DataAttribute>屬性來指定基礎儲存欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="930e5-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property on the <xref:System.Data.Linq.Mapping.DataAttribute> attribute to designate the name of an underlying storage field.</span></span>  
  
 <span data-ttu-id="930e5-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>。</span><span class="sxs-lookup"><span data-stu-id="930e5-104">For code examples, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a><span data-ttu-id="930e5-105">若要指定基礎儲存欄位的名稱</span><span class="sxs-lookup"><span data-stu-id="930e5-105">To specify the name of an underlying storage field</span></span>  
  
1. <span data-ttu-id="930e5-106">將 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="930e5-106">Add the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="930e5-107">指定欄位名稱做為 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 屬性 (Property) 的值。</span><span class="sxs-lookup"><span data-stu-id="930e5-107">Assign the name of the field as the value of the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="930e5-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="930e5-108">See also</span></span>

- [<span data-ttu-id="930e5-109">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="930e5-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="930e5-110">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="930e5-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
