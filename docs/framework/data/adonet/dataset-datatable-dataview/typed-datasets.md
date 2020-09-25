---
title: 具類型資料集
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 4648d49b1d7419d61a3a000404f42e0d02d25786
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198440"
---
# <a name="typed-datasets"></a>具類型資料集

<xref:System.Data.DataSet> 可透過弱型別變數，使用晚期繫結存取值，也可透過強型別變數存取資料。 您可以使用易記的名稱和強型別變數來存取屬於 **資料集** 一部分的資料表和資料行。  
  
 具類型 **資料集** 是衍生自 **資料集**的類別。 因此，它會繼承 **資料集**的所有方法、事件和屬性。 此外，具類型的 **資料集會** 提供強型別方法、事件和屬性。 換句話說，您可以依照名稱存取資料表和資料行，而不需要使用集合架構的方法。 除了改良的程式碼可讀性之外，具類型的 **資料集** 也可讓 Visual Studio .NET 程式碼編輯器在您輸入時自動完成行。  
  
 此外，強型別 **資料集** 可讓您在編譯時期，以正確的型別來存取值。 使用強型別 **資料集**時，在編譯器代碼時（而不是在執行時間），會攔截到類型不符的錯誤。  
  
## <a name="in-this-section"></a>本節內容  

 [產生強類型資料集](generating-strongly-typed-datasets.md)  
 描述如何建立和使用強型別 **資料集**。  
  
 [註釋具類型資料集](annotating-typed-datasets.md)  
 描述如何標注 XML 架構定義語言 (XSD) 架構，用來產生強型別 **資料集**，以便在不改變基礎架構的情況下，提供 **資料集** 元素的易記名稱。  
  
## <a name="see-also"></a>另請參閱

- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
