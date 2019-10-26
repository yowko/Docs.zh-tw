---
title: LINQ to XML 資料系結範例
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920934"
---
# <a name="linq-to-xml-data-binding-sample"></a>LINQ to XML 資料系結範例

本文描述 LinqToXmlDataBinding 範例，這是將使用者介面元件系結至內嵌 XML 資料來源的 Windows Presentation Foundation （WPF）應用程式。

## <a name="overview"></a>總覽

LinqToXmlDataBinding 範例是包含C#和 XAML 原始程式檔的 WINDOWS PRESENTATION FOUNDATION （WPF）應用程式。 內嵌的 XML 檔會定義書籍的清單。 應用程式可讓使用者查看、新增、刪除和編輯書籍專案。

有兩個主要來源檔案：

- [L2DBForm.xaml](l2dbform-xaml-source-code.md) 包含適用於主視窗之使用者介面 (UI) 的 XAML 宣告程式碼。 它也包含一個視窗資源區段，其中定義了書籍清單的資料提供者和內嵌的 XML 檔。

- [L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) 包含與 UI 建立關聯的初始化與事件處理方法。

主視窗分為下列四個 UI 垂直區段：

- **XML**：顯示內嵌書籍清單的 XML 原始檔。

- **書籍清單**：將書籍項目顯示為標準文字，並讓使用者選取和刪除個別的項目。

- **編輯選取的書籍**：可讓使用者編輯與目前所選之書籍項目相關聯的值。

- **加入新的書籍**：可根據使用者輸入的值，建立新的書籍項目。

## <a name="run-the-sample"></a>執行範例

本節說明如何在 Visual Studio 中建立和建立 LinqToXmlDataBinding 專案，以及如何執行產生的 LinqToXmlDataBinding Windows Presentation Foundation （WPF）應用程式。

### <a name="create-the-project"></a>建立專案

1. 開啟 Visual Studio，然後建立名為 **LinqToXmlDataBinding** 的 C# **WPF 應用程式**。

   專案應該將目標設定為 .NET Framework 3.5 (或更新版本)。

1. 如果尚未存在，加入下列 .NET 組件的專案參考：

    - System.Data
    - System.Data.DataSetExtensions
    - System.Xml
    - System.Xml

1. 按 **Ctrl**+**Shift**+**B** 來建置方案，然後按 **F5** 鍵來執行。

   專案的編譯應該沒有錯誤，而且應該當做一般 WPF 應用程式執行。

### <a name="add-code"></a>新增程式碼

1. 在 [方案總管] 中，將原始程式檔 **Window1.xaml** 重新命名為 **L2XDBForm.xaml**。

   相依的來源檔案 Window1.xaml.cs 會自動重新命名為 L2XDBForm.xaml.cs。

1. 以[l2dbform.xaml 程式碼](l2dbform-xaml-source-code.md)取代**l2xdbform.xaml**檔案中找到的原始程式碼。 使用 XAML 原始碼檢視來使用這個檔案。

1. 同樣地，使用[L2DBForm.xaml.cs 原始程式碼](l2dbform-xaml-cs-source-code.md)取代**L2XDBForm.xaml.cs**中的來源。

1. 在檔案**app.xaml**中，將所有出現的字串**Window1.xaml**取代為**l2xdbform.xaml**。

1. 按 **Ctrl**+**Shift**+**B** 來建置方案。

### <a name="run-the-app"></a>執行應用程式

LinqToXmlDataBinding 應用程式可讓使用者查看及操作儲存為內嵌 XML 元素的書籍清單。 按**f5** （開始偵錯工具）或**Ctrl**+**F5** （[啟動但不進行偵錯工具]）來執行應用程式。

標題為 [使用 LINQ to XML 進行 WPF 資料繫結] 的程式視窗隨即出現。

UI 的上方區段會顯示代表書籍清單的原始**XML** 。 它會使用 WPF <xref:System.Windows.Controls.TextBlock> 控制項顯示，不會透過滑鼠或鍵盤啟用互動。

第二個垂直區段標示為 [書籍清單]，會將書籍顯示為純文字排序的清單。 它使用 <xref:System.Windows.Controls.ListBox> 控制項，可透過滑鼠或鍵盤進行選取。

### <a name="add-and-delete-books"></a>新增和刪除書籍

若要將新的書籍加入清單中，請在 [ **ID** ] 和 [**值**] 中輸入值，<xref:System.Windows.Controls.TextBox> 控制項的最後一節 [**加入新書籍**]，然後選取 [**新增書籍**]。 本書會附加至書籍和 XML 清單中的清單。 這個程式不會驗證輸入值。

若要從清單中刪除現有的書籍，請在 [**書籍清單**] 區段中選取它，然後選取 [**移除選取的書籍**]。 書籍專案會從書籍和原始 XML 來源清單中移除。

### <a name="edit-a-book-entry"></a>編輯書籍專案

1. 在第二個 [書籍清單] 區段中選取書籍項目。

   其目前的值會顯示在 [**編輯選取的書籍**] 區段中。

1. 使用鍵盤編輯值。 一旦 <xref:System.Windows.Controls.TextBox> 控制項失去焦點，變更就會自動傳播至 XML 來源和書籍清單。
