---
title: 如何： 建立主版詳細資料表單使用兩個 Windows Form DataGridView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: 328970c5cc14669770793070942dd32f0144c159
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002797"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>如何：使用兩個 Windows Form DataGridView 控制項建立主從式表單
下列程式碼範例會使用兩個 <xref:System.Windows.Forms.DataGridView> 控制項繫結至兩個 <xref:System.Windows.Forms.BindingSource> 元件來建立主從式表單。 資料來源是 <xref:System.Data.DataSet>，包含來自 Northwind SQL Server 範例資料庫的 `Customers` 和 `Orders` 資料表，以及透過 `CustomerID` 資料行和這兩者產生關聯的 <xref:System.Data.DataRelation>。  
  
 一個 <xref:System.Windows.Forms.BindingSource> 會繫結至資料集中的父代 `Customers` 資料表。 此資料會顯示在 <xref:System.Windows.Forms.DataGridView> 主控制項。 其他 <xref:System.Windows.Forms.BindingSource> 會繫結至第一個資料連接器。 第二個 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性會設為 <xref:System.Data.DataRelation> 的名稱。 這會導致相關的 <xref:System.Windows.Forms.DataGridView> 詳細資料控制項顯示 `Orders` 子資料表的資料列，對應到 <xref:System.Windows.Forms.DataGridView> 主控制項中的目前資料列。  
  
 如需這個程式碼範例的完整說明，請參閱 <<c0> [ 逐步解說： 建立主版/詳細表單使用兩個 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
 System、System.Data、System.Windows.Forms 和 System.XML 組件的參考。   
  
-   Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [逐步解說：使用兩個 Windows Forms DataGridView 控制項建立主從式表單](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 [在 Windows Forms DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)
