---
title: 作法：將資料行表示為時間戳記或版本資料行
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: ef99e0420b328f94686e08256ecf229000467810
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793495"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="f28e8-102">作法：將資料行表示為時間戳記或版本資料行</span><span class="sxs-lookup"><span data-stu-id="f28e8-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="f28e8-103">使用屬性（<xref:System.Data.Linq.Mapping.ColumnAttribute> attribute）的屬性（property）來指定欄位或屬性（property），以表示保存資料庫時間戳記或版本號碼的資料庫資料行。<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f28e8-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="f28e8-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="f28e8-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="f28e8-105">若要指定欄位或屬性以表示時間戳記或版本資料行</span><span class="sxs-lookup"><span data-stu-id="f28e8-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1. <span data-ttu-id="f28e8-106">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="f28e8-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="f28e8-107">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 (Property) 值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f28e8-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f28e8-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f28e8-108">See also</span></span>

- [<span data-ttu-id="f28e8-109">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="f28e8-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="f28e8-110">如何：指定測試並行衝突的成員</span><span class="sxs-lookup"><span data-stu-id="f28e8-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="f28e8-111">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="f28e8-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
