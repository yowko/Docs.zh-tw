---
title: "如何︰ 使用 LINQ (Visual Basic) 來呼叫預存程序 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: abc3970fc5ab6f4a2f4b67b5efa2b19afb07337b
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>如何：使用 LINQ 呼叫預存程序 (Visual Basic)
語言整合查詢 (LINQ) 可讓您更容易存取的資料庫資訊，包括資料庫物件，例如預存程序。  
  
 下列範例示範如何建立 SQL Server 資料庫中呼叫預存程序的應用程式。 此範例示範如何呼叫資料庫中的兩個不同的預存程序。 每個程序傳回查詢的結果。 一個程序會使用輸入的參數，和其他程序不接受參數。  
  
 本主題中的範例使用 Northwind 範例資料庫。 如果您的開發電腦上沒有 Northwind 範例資料庫，您可以下載從[Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkID=98088)網站。 如需指示，請參閱[下載範例資料庫](https://msdn.microsoft.com/library/bb399411)。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>若要建立資料庫的連接  
  
1.  在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫總管**上**檢視**功能表。  
  
2.  以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**然後按一下 **加入連接**。  
  
3.  指定有效的連接至 Northwind 範例資料庫。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>若要將專案加入包含 LINQ to SQL 檔案  
  
1.  在 Visual Studio 中，在**檔案**功能表上，指向**新增**然後按一下 **專案**。 選取 Visual Basic **Windows Form 應用程式**做為專案類型。  
  
2.  在 [專案] **Walkthrough: Adding Controls to a Worksheet at Run Time in an VSTO Add-in project** 功能表中，按一下 [加入新項目] ****。 選取**LINQ to SQL 類別**項目範本。  
  
3.  將檔案命名`northwind.dbml`。 按一下 [加入] ****。 Northwind.dbml 檔案的開啟物件關聯式設計工具 （O/R 設計工具）。  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>將預存程序加入至 O/R 設計工具  
  
1.  在**伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。 展開**預存程序**資料夾。  
  
     如果您已關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。  
  
2.  按一下 **依年份銷售**預存程序，並將它拖曳至設計工具的右窗格。 按一下  **Ten Most Expensive Products**預存程序將它拖曳至設計工具的右窗格。  
  
3.  儲存變更並關閉設計工具。  
  
4.  儲存您的專案。  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>加入程式碼以顯示預存程序的結果  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>控制項拖曳到預設的 Windows Form 專案，Form1。</xref:System.Windows.Forms.DataGridView>  
  
2.  按兩下 Form1 加入程式碼以其`Load`事件。  
  
3.  當您加入至 O/R 設計工具的預存程序時，設計工具加入<xref:System.Data.Linq.DataContext>物件，為您的專案。</xref:System.Data.Linq.DataContext> 此物件包含的程式碼，您必須具有存取上述程序。 <xref:System.Data.Linq.DataContext>物件的專案命名為基礎的.dbml 檔案名稱。</xref:System.Data.Linq.DataContext> 針對此專案，<xref:System.Data.Linq.DataContext>物件名為`northwindDataContext`。</xref:System.Data.Linq.DataContext>  
  
     您可以建立的執行個體<xref:System.Data.Linq.DataContext>O/R 設計工具所指定程式碼與呼叫中的預存程序的方法。</xref:System.Data.Linq.DataContext> 繫結至<xref:System.Windows.Forms.DataGridView>物件，您可能必須強制查詢立即執行，藉由呼叫<xref:System.Linq.Enumerable.ToList%2A>方法的預存程序的結果。</xref:System.Linq.Enumerable.ToList%2A> </xref:System.Windows.Forms.DataGridView>  
  
     加入下列程式碼以`Load`事件呼叫預存程序公開為資料內容的方法。  
  
     [!code-vb[VbLINQtoSQLHowTos #&1;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos #&2;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  按 F5 執行您的專案，並檢視結果。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [查詢](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)   
 [DataContext 方法 （O/R 設計工具）](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)   
 [如何︰ 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)

