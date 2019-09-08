---
title: 使用者定義函式
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 40697da4fe678668f8f7ecda86abebf40da7b973
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792299"
---
# <a name="user-defined-functions"></a>使用者定義函式
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會使用物件模型 (Object Model) 中的方法來表示使用者定義函式。 您可套用 <xref:System.Data.Linq.Mapping.FunctionAttribute> 屬性 (Attribute) 和 (視需要) 套用 <xref:System.Data.Linq.Mapping.ParameterAttribute> 屬性，將方法指定為函式。 如需詳細資訊，請參閱[LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)。  
  
 若要避免 <xref:System.InvalidOperationException>，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的使用者定義函式必須為下列其中一種形式：  
  
- 包裝為具有正確對應屬性之方法呼叫的函式。 如需詳細資訊，請參閱以[屬性為基礎的對應](attribute-based-mapping.md)。  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 特有的靜態 SQL 方法。  
  
- .NET Framework 方法所支援的函式。  
  
 本節中的主題顯示自行撰寫程式碼時，如何在應用程式中形成和呼叫這些方法。 使用 Visual Studio 的開發人員通常會使用物件關聯式設計工具來對應使用者定義的函數。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：使用純量值使用者定義函數](how-to-use-scalar-valued-user-defined-functions.md)  
 描述如何實作可傳回純量值的函式。  
  
 [如何：使用資料表值使用者定義函數](how-to-use-table-valued-user-defined-functions.md)  
 描述如何實作可傳回資料表值的函式。  
  
 [如何：以內嵌方式呼叫使用者定義函數](how-to-call-user-defined-functions-inline.md)  
 描述如何對函式進行內嵌 (Inline) 呼叫，以及當呼叫成為內嵌時的執行差異。
