---
title: 如何：處置系統資源
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: dd15c6746628f45b072d46eea40051ed9afb7921
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403494"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>如何：處置系統資源 (Visual Basic)
您可以使用 `Using` 區塊，確保當您的程式碼結束區塊時，系統會處置資源。 如果您使用的系統資源會耗用大量的記憶體，或其他元件也想要使用，這就很有用。  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>若要在程式碼完成時處置資料庫連接  
  
1. 請確定您在來源檔案的開頭包含資料庫連接的適當[Imports 語句（.Net 命名空間和類型）](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) （在此案例中為 <xref:System.Data.SqlClient> ）。  
  
2. `Using`使用和語句建立區塊 `Using` `End Using` 。 在區塊內，放入處理資料庫連接的程式碼。  
  
3. 宣告連接，並建立它的實例作為語句的一部分 `Using` 。  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     無論您如何結束區塊，系統都會處置資源，包括未處理之例外狀況的情況。  
  
     請注意，您無法 `sqc` 從區塊外部存取 `Using` ，因為它的範圍限制為區塊。  
  
     您可以在系統資源（例如檔案控制代碼或 COM 包裝函式）上使用這項相同的技術。 當您想要在 `Using` 結束區塊之後讓其他元件有可用的資源時，請使用區塊 `Using` 。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.SqlClient.SqlConnection>
- [控制流程](index.md)
- [決策結構](decision-structures.md)
- [迴圈結構](loop-structures.md)
- [其他控制結構](other-control-structures.md)
- [巢狀控制結構](nested-control-structures.md)
- [Using 語句](../../../language-reference/statements/using-statement.md)
