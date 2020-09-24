---
title: 繼承支援
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 7673e69458d5c1af854747c43ba463332a9cd588
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158249"
---
# <a name="inheritance-support"></a>繼承支援

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援 *單一資料表對應*。 換句話說，完整的繼承階層架構 (Inheritance Hierarchy) 會儲存在單一資料庫資料表中。 這張資料表包含整個階層架構中所有可能之資料行的平面聯集   (等位是將兩個數據表結合成一個資料表的結果，而該資料表具有存在於原始資料表中的資料列 ) 。在資料行中，每個資料列都有 null，而這些資料行不會套用至資料列所代表之實例的類型。  
  
 單一資料表對應策略是最簡單的繼承表示，並且可以在許多不同類別的查詢中提供良好的效能特性。  
  
 若要在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中實作這個對應，則必須在繼承階層架構的根類別中指定屬性 (Attribute) 和屬性的屬性 (Attribute Property)。 如需詳細資訊，請參閱 [如何：對應繼承](how-to-map-inheritance-hierarchies.md)階層架構。  
  
 使用 Visual Studio 的開發人員也可以使用物件關聯式設計工具來對應繼承階層架構。  
  
## <a name="see-also"></a>另請參閱

- [背景資訊](background-information.md)
