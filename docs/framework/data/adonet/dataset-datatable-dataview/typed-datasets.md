---
title: 具類型資料集
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 33876cb9f614a93cab2fa3fd9d056f94dd1e9038
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203160"
---
# <a name="typed-datasets"></a>具類型資料集
<xref:System.Data.DataSet> 可透過弱型別變數，使用晚期繫結存取值，也可透過強型別變數存取資料。 您可以使用使用者易記名稱和強型別變數來存取**資料集**一部分的資料表和資料行。  
  
 具類型**資料集**是衍生自**資料集**的類別。 因此, 它會繼承**資料集**的所有方法、事件和屬性。 此外, 具類型的**資料集**提供強型別方法、事件和屬性。 換句話說，您可以依照名稱存取資料表和資料行，而不需要使用集合架構的方法。 除了增強的程式碼可讀性之外, 具類型的**資料集**也可讓 Visual Studio 的 .net 程式碼編輯器在您輸入時自動完成行。  
  
 此外, 強型別**資料集**會在編譯時期提供值的存取權做為正確的類型。 使用強型別**資料集**時, 在編譯器代碼而不是在執行時間時, 會攔截到類型不符的錯誤。  
  
## <a name="in-this-section"></a>本節內容  
 [產生強型別資料集](generating-strongly-typed-datasets.md)  
 描述如何建立和使用強型別**資料集**。  
  
 [註釋具類型資料集](annotating-typed-datasets.md)  
 描述如何標注用來產生強型別**資料集**的 XML 架構定義語言 (XSD) 架構, 以便在不改變基礎架構的情況下, 為**DataSet**元素提供易記名稱。  
  
## <a name="see-also"></a>另請參閱

- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
