---
title: HOW TO：處置系統資源 (Visual Basic)
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
ms.openlocfilehash: 798650bbefc0c5b2ac097b87ab44a2b380117939
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523216"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>HOW TO：處置系統資源 (Visual Basic)
您可以使用`Using`區塊，以確保系統處置資源的程式碼結束該區塊時。 這非常有用，如果您使用的，會耗用大量記憶體，或其他元件也會想要使用的系統資源。  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>若要結束您的程式碼時，在資料庫連接的處理  
  
1.  請確定您包含適當[Imports 陳述式 （.NET 命名空間和類型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)原始程式檔的開頭資料庫連接 (在此情況下， <xref:System.Data.SqlClient>)。  
  
2.  建立`Using`含有區塊`Using`和`End Using`陳述式。 在區塊內，將資料庫連接處理的程式碼。  
  
3.  宣告連接並建立它的執行個體的一部分`Using`陳述式。  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     系統會處置的資源，無論您如何結束區塊中，包括處理的例外狀況的情況。  
  
     請注意，您無法存取`sqc`從外部`Using`封鎖，因為其範圍僅限於該區塊。  
  
     您可以使用這項技術的系統資源，例如檔案控制代碼或 COM 包裝函式。 您使用`Using`當您想要確定保留資源供其他元件之後結束, 時，封鎖`Using`區塊。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Data.SqlClient.SqlConnection>
- [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [決策結構](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [其他控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [巢狀控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)
