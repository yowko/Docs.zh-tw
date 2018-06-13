---
title: 如何：將引號放入字串中 (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 7fcc2e8692880f1e5c2b8df807cf7943a5575c56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534829"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="a4e6a-102">如何：將引號放入字串中 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a4e6a-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="a4e6a-103">您有時可能想要將引號 (" ") 放入文字字串中。</span><span class="sxs-lookup"><span data-stu-id="a4e6a-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="a4e6a-104">例如: </span><span class="sxs-lookup"><span data-stu-id="a4e6a-104">For example:</span></span>  
  
 <span data-ttu-id="a4e6a-105">She said, "You deserve a treat!"</span><span class="sxs-lookup"><span data-stu-id="a4e6a-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="a4e6a-106">或者，您也可以使用<xref:Microsoft.VisualBasic.ControlChars.Quote>欄位做為常數。</span><span class="sxs-lookup"><span data-stu-id="a4e6a-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="a4e6a-107">將引號放入您的程式碼中的字串</span><span class="sxs-lookup"><span data-stu-id="a4e6a-107">To place quotation marks in a string in your code</span></span>  
  
1.  <span data-ttu-id="a4e6a-108">在 Visual Basic 中，插入資料列中的兩個引號做為內嵌的雙引號。</span><span class="sxs-lookup"><span data-stu-id="a4e6a-108">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="a4e6a-109">在 Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]，插入逸出序列\\"做為內嵌的雙引號。</span><span class="sxs-lookup"><span data-stu-id="a4e6a-109">In Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="a4e6a-110">例如，若要建立前置字串，請使用下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="a4e6a-110">For example, to create the preceding string, use the following code.</span></span>  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     <span data-ttu-id="a4e6a-111">-或-</span><span class="sxs-lookup"><span data-stu-id="a4e6a-111">-or-</span></span>  
  
2.  <span data-ttu-id="a4e6a-112">針對引號插入 ASCII 或 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="a4e6a-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="a4e6a-113">在 Visual Basic 中使用 ASCII 字元 (34)。</span><span class="sxs-lookup"><span data-stu-id="a4e6a-113">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="a4e6a-114">在 Visual C# 中，使用 Unicode 字元 (\u0022)。</span><span class="sxs-lookup"><span data-stu-id="a4e6a-114">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a4e6a-115">在此範例中，您無法使用 \u0022，因為不能使用表明是基本字元集中字元的通用字元名稱。</span><span class="sxs-lookup"><span data-stu-id="a4e6a-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="a4e6a-116">否則，您會產生 c3851。</span><span class="sxs-lookup"><span data-stu-id="a4e6a-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="a4e6a-117">如需詳細資訊，請參閱[編譯器錯誤 C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851)。</span><span class="sxs-lookup"><span data-stu-id="a4e6a-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="a4e6a-118">-或-</span><span class="sxs-lookup"><span data-stu-id="a4e6a-118">-or-</span></span>  
  
3.  <span data-ttu-id="a4e6a-119">您也可以定義字元的常數，並且在需要時使用它。</span><span class="sxs-lookup"><span data-stu-id="a4e6a-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a4e6a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4e6a-120">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:Microsoft.VisualBasic.ControlChars.Quote>  
 [<span data-ttu-id="a4e6a-121">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="a4e6a-121">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="a4e6a-122">操作說明：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="a4e6a-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="a4e6a-123">操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="a4e6a-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="a4e6a-124">操作說明：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="a4e6a-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="a4e6a-125">操作說明：在 Windows Forms TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="a4e6a-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="a4e6a-126">操作說明：在 Windows Forms TextBox 控制項中檢視多行</span><span class="sxs-lookup"><span data-stu-id="a4e6a-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="a4e6a-127">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="a4e6a-127">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
