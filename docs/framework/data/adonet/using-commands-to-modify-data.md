---
title: 使用命令修改資料
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 34c73549f18cd4bebb8caf842b252828b7f0a185
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780569"
---
# <a name="using-commands-to-modify-data"></a>使用命令修改資料
您可以使用 .NET Framework 資料提供者來執行預存程序或資料定義語言陳述式 (例如 CREATE TABLE 和 ALTER COLUMN)，以執行資料庫或目錄的結構描述管理。 這些命令不會以查詢的形式傳回資料列，因此**Command**物件會提供**ExecuteNonQuery**來處理它們。  
  
 除了使用**ExecuteNonQuery**來修改架構，您也可以使用這個方法來處理修改資料的 SQL 語句，但不會傳回資料列，例如 INSERT、UPDATE 和 DELETE。  
  
 雖然**ExecuteNonQuery**方法不會傳回資料列，但輸入和輸出參數和傳回值可透過**Command**物件的**parameters**集合來傳遞和傳回。  
  
## <a name="in-this-section"></a>本節內容  
 [更新資料來源中的資料](updating-data-in-a-data-source.md)  
 說明如何執行修改資料庫資料的命令或預存程序。  
  
 [執行目錄作業](performing-catalog-operations.md)  
 說明如何執行修改資料庫結構描述的命令。  
  
## <a name="see-also"></a>另請參閱

- [在 ADO.NET 中擷取和修改資料](retrieving-and-modifying-data.md)
- [命令和參數](commands-and-parameters.md)
- [ADO.NET 概觀](ado-net-overview.md)
