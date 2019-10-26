---
title: L2DBForm.xaml.cs 原始程式碼
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 882699a76eab3c291cd92c298287bc5d28fb08e1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920857"
---
# <a name="l2dbformxamlcs-source-code"></a><span data-ttu-id="4d508-102">L2DBForm.xaml.cs 原始程式碼</span><span class="sxs-lookup"><span data-stu-id="4d508-102">L2DBForm.xaml.cs source code</span></span>

<span data-ttu-id="4d508-103">此頁面包含C# *L2DBForm.xaml.cs*檔案中原始程式碼的內容與描述。</span><span class="sxs-lookup"><span data-stu-id="4d508-103">This page contains the contents and description of the C# source code in the file *L2DBForm.xaml.cs*.</span></span> <span data-ttu-id="4d508-104">此檔案中所包含的 L2XDBForm 部分類別可分為三個邏輯區段：資料成員、`OnRemove` 以及 `OnAddBook` 按鈕 Click 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4d508-104">The L2XDBForm partial class contained in this file can be divided into three logical sections: data members and the `OnRemove` and `OnAddBook` button click event handlers.</span></span>

## <a name="data-members"></a><span data-ttu-id="4d508-105">資料成員</span><span class="sxs-lookup"><span data-stu-id="4d508-105">Data members</span></span>

<span data-ttu-id="4d508-106">系統會使用兩個私有資料成員，將此類別與 L2DBForm.xaml 中所使用的視窗資源產生關聯。</span><span class="sxs-lookup"><span data-stu-id="4d508-106">Two private data members are used to associate this class to the window resources used in *L2DBForm.xaml*.</span></span>

- <span data-ttu-id="4d508-107">系統會將命名空間變數 `myBooks` 初始化為 `"http://www.mybooks.com"`。</span><span class="sxs-lookup"><span data-stu-id="4d508-107">The namespace variable `myBooks` is initialized to `"http://www.mybooks.com"`.</span></span>

- <span data-ttu-id="4d508-108">利用下行，建構函式中的成員 `bookList` 會被初始化為 L2DBForm.xaml 中的 CDATA 字串：</span><span class="sxs-lookup"><span data-stu-id="4d508-108">The member `bookList` is initialized in the constructor to the CDATA string in *L2DBForm.xaml* with the following line:</span></span>

    ```csharp
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a><span data-ttu-id="4d508-109">OnAddBook 事件處理常式</span><span class="sxs-lookup"><span data-stu-id="4d508-109">OnAddBook event handler</span></span>

<span data-ttu-id="4d508-110">這個方法包含下列三個陳述式：</span><span class="sxs-lookup"><span data-stu-id="4d508-110">This method contains the following three statements:</span></span>

- <span data-ttu-id="4d508-111">第一個條件陳述式用於輸入驗證。</span><span class="sxs-lookup"><span data-stu-id="4d508-111">The first conditional statement is used for input validation.</span></span>

- <span data-ttu-id="4d508-112">第二個陳述式會從使用者在 [加入新的書籍] 使用者介面 (UI) 區段中輸入的字串值，建立新的 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="4d508-112">The second statement creates a new <xref:System.Xml.Linq.XElement> from the string values the user entered in the **Add New Book** user interface (UI) section.</span></span>

- <span data-ttu-id="4d508-113">最後一個陳述式會將這個新書籍項目新增至 L2DBForm.xaml 的資料提供者中。</span><span class="sxs-lookup"><span data-stu-id="4d508-113">The last statement adds this new book element to the data provider in *L2DBForm.xaml*.</span></span> <span data-ttu-id="4d508-114">因此，動態資料繫結將會使用這個新項目，自動更新 UI；不需要使用者提供的任何額外程式碼。</span><span class="sxs-lookup"><span data-stu-id="4d508-114">Consequently, dynamic data binding will automatically update the UI with this new item; no extra user-supplied code is required.</span></span>

## <a name="onremove-event-handler"></a><span data-ttu-id="4d508-115">OnRemove 事件處理常式</span><span class="sxs-lookup"><span data-stu-id="4d508-115">OnRemove event handler</span></span>

<span data-ttu-id="4d508-116">`OnRemove` 處理常式比 `OnAddBook` 處理常式複雜的原因有兩個。</span><span class="sxs-lookup"><span data-stu-id="4d508-116">The `OnRemove` handler is more complicated than the `OnAddBook` handler for two reasons.</span></span> <span data-ttu-id="4d508-117">第一，原始 XML 包含保留的空白字元，因此，相符的新行 (Newline) 也必須利用書籍項目移除。</span><span class="sxs-lookup"><span data-stu-id="4d508-117">First, because the raw XML contains preserved white space, matching newlines must also be removed with the book entry.</span></span> <span data-ttu-id="4d508-118">第二，為了方便起見，在已刪除項目上的選項會重新設定為清單中的前一個選項。</span><span class="sxs-lookup"><span data-stu-id="4d508-118">Second, as a convenience, the selection, which was on the deleted item, is reset to the previous one in the list.</span></span>

<span data-ttu-id="4d508-119">不過，移除所選書籍項目的核心工作僅由兩個陳述式完成：</span><span class="sxs-lookup"><span data-stu-id="4d508-119">However, the core work of removing the selected book item is accomplished by only two statements:</span></span>

- <span data-ttu-id="4d508-120">首先，系統會擷取清單方塊中，與目前所選項目相關聯的書籍項目：</span><span class="sxs-lookup"><span data-stu-id="4d508-120">First, the book element associated with the currently selected item in the list box is retrieved:</span></span>

    ```csharp
    XElement selBook = (XElement)lbBooks.SelectedItem;
    ```

- <span data-ttu-id="4d508-121">接著，這個項目會從資料提供者刪除：</span><span class="sxs-lookup"><span data-stu-id="4d508-121">Then, this element is deleted from the data provider:</span></span>

    ```csharp
    selBook.Remove();
    ```

<span data-ttu-id="4d508-122">再次提醒，動態資料繫結會確保程式的 UI 會自動更新。</span><span class="sxs-lookup"><span data-stu-id="4d508-122">Again, dynamic data binding assures that the program's UI is automatically updated.</span></span>

## <a name="example"></a><span data-ttu-id="4d508-123">範例</span><span class="sxs-lookup"><span data-stu-id="4d508-123">Example</span></span>

### <a name="code"></a><span data-ttu-id="4d508-124">程式碼</span><span class="sxs-lookup"><span data-stu-id="4d508-124">Code</span></span>

```csharp
using System;
using System.Linq;
using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Input;
using System.Xml;
using System.Xml.Linq;

namespace LinqToXmlDataBinding {
    /// <summary>
    /// Interaction logic for L2XDBForm.xaml
    /// </summary>

    public partial class L2XDBForm : System.Windows.Window
    {
        XNamespace mybooks = "http://www.mybooks.com";
        XElement bookList;

        public L2XDBForm()
        {
            InitializeComponent();
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
        }

        void OnRemoveBook(object sender, EventArgs e)
        {
            int index = lbBooks.SelectedIndex;
            if (index < 0) return;

            XElement selBook = (XElement)lbBooks.SelectedItem;
            //Get next node before removing element.
            XNode nextNode = selBook.NextNode;
            selBook.Remove();

            //Remove any matching newline node.
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))
            { nextNode.Remove(); }

            //Set selected item.
            if (lbBooks.Items.Count > 0)
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }
        }

        void OnAddBook(object sender, EventArgs e)
        {
            if (String.IsNullOrEmpty(tbAddID.Text) ||
                String.IsNullOrEmpty(tbAddValue.Text))
            {
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");
                return;
            }
            XElement newBook = new XElement(
                                mybooks + "book",
                                new XAttribute("id", tbAddID.Text),
                                tbAddValue.Text);
            bookList.Add("  ", newBook, "\r\n");
        }
    }
}
```

### <a name="comments"></a><span data-ttu-id="4d508-125">註解</span><span class="sxs-lookup"><span data-stu-id="4d508-125">Comments</span></span>

<span data-ttu-id="4d508-126">如需這些處理常式的相關聯 XAML 原始碼，請參閱 [L2DBForm.xaml 原始程式碼](l2dbform-xaml-source-code.md)。</span><span class="sxs-lookup"><span data-stu-id="4d508-126">For the associated XAML source for these handlers, see [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d508-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d508-127">See also</span></span>

- [<span data-ttu-id="4d508-128">逐步解說：LinqToXmlDataBinding 範例</span><span class="sxs-lookup"><span data-stu-id="4d508-128">Walkthrough: LinqToXmlDataBinding example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="4d508-129">L2DBForm.xaml 來源程式碼</span><span class="sxs-lookup"><span data-stu-id="4d508-129">L2DBForm.xaml source code</span></span>](l2dbform-xaml-source-code.md)
