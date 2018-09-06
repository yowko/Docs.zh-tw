---
title: 使用命令修改資料
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 6388eecb2e96970f47383b61985d672bd0419a1e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864140"
---
# <a name="using-commands-to-modify-data"></a>使用命令修改資料
您可以使用 .NET Framework 資料提供者來執行預存程序或資料定義語言陳述式 (例如 CREATE TABLE 和 ALTER COLUMN)，以執行資料庫或目錄的結構描述管理。 這些命令不會傳回資料列像查詢一樣，因此**命令**物件提供**ExecuteNonQuery**加以處理。  
  
 除了使用**ExecuteNonQuery**修改結構描述，您也可以使用這個方法來處理 SQL 陳述式所修改的資料，但是，不傳回資料列，例如插入、 更新和刪除。  
  
 雖然不會傳回資料列**ExecuteNonQuery**方法、 輸入和輸出參數和傳回值可以傳遞和傳回透過**參數**集合**命令**物件。  
  
## <a name="in-this-section"></a>本節內容  
 [更新資料來源中的資料](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 說明如何執行修改資料庫資料的命令或預存程序。  
  
 [執行目錄作業](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 說明如何執行修改資料庫結構描述的命令。  
  
## <a name="see-also"></a>另請參閱  
 [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
