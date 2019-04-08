---
title: 具類型資料集
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 92ed3f8fd392238785fd2d205668f14fe477f2b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098646"
---
# <a name="typed-datasets"></a>具類型資料集
<xref:System.Data.DataSet> 可透過弱型別變數，使用晚期繫結存取值，也可透過強型別變數存取資料。 資料表和資料行屬於**資料集**可以使用好記名稱和存取強型別變數。  
  
 具型別**資料集**是衍生自類別**DataSet**。 因此，所有方法、 事件和屬性的都繼承**資料集**。 此外，具型別**資料集**提供強型別的方法、 事件和屬性。 換句話說，您可以依照名稱存取資料表和資料行，而不需要使用集合架構的方法。 除了更容易閱讀的程式碼，具型別**資料集**也可讓 Visual Studio.NET 程式碼編輯器，當您輸入時自動完成輸入行。  
  
 此外，強型別**資料集**提供存取值為正確的類型，在編譯時期。 使用強型別**資料集**，程式碼是編譯而不會在執行階段時攔截類型不符的錯誤。  
  
## <a name="in-this-section"></a>本節內容  
 [產生強類型資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 描述如何建立和使用強型別**資料集**。  
  
 [註釋具類型資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 描述如何用來產生強類型的 XML 結構描述定義語言 (XSD) 結構描述加上註解**資料集**，以提供**DataSet**項目的易記名稱，而不需要變更基礎結構描述。  
  
## <a name="see-also"></a>另請參閱

- [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET Managed 提供者和DataSet開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
