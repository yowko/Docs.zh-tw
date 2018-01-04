---
title: "Windows Form 和控制項中的國際字型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e7b6574e452faf4f0396f7633ba7f21519948262
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="d9319-102">Windows Form 和控制項中的國際字型</span><span class="sxs-lookup"><span data-stu-id="d9319-102">International Fonts in Windows Forms and Controls</span></span>
<span data-ttu-id="d9319-103">國際應用程式中選取字型的建議的方法是盡可能使用字型遞補。</span><span class="sxs-lookup"><span data-stu-id="d9319-103">In International applications the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="d9319-104">所屬字型遞補表示系統決定指令碼字元。</span><span class="sxs-lookup"><span data-stu-id="d9319-104">Font fallback means that the system determines what script the character belongs to.</span></span>  
  
## <a name="using-font-fallback"></a><span data-ttu-id="d9319-105">使用字型遞補</span><span class="sxs-lookup"><span data-stu-id="d9319-105">Using Font Fallback</span></span>  
 <span data-ttu-id="d9319-106">若要利用這項功能，請勿設定<xref:System.Drawing.Font>表單或其他任何項目屬性。</span><span class="sxs-lookup"><span data-stu-id="d9319-106">To take advantage of this feature, do not set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="d9319-107">應用程式會自動使用預設系統字型，這與不同作業系統的當地語系化語言到另一個。</span><span class="sxs-lookup"><span data-stu-id="d9319-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="d9319-108">應用程式執行時，系統將會自動提供正確的字型，在作業系統中選取的文化特性。</span><span class="sxs-lookup"><span data-stu-id="d9319-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>  
  
 <span data-ttu-id="d9319-109">沒有規則的例外狀況都不設定字型，這是變更字型樣式。</span><span class="sxs-lookup"><span data-stu-id="d9319-109">There is an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="d9319-110">這可能是很重要的應用程式中的使用者按一下按鈕，以粗體文字在文字方塊中出現。</span><span class="sxs-lookup"><span data-stu-id="d9319-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="d9319-111">若要這樣做，您可以撰寫函式來變更文字方塊的字型樣式，要以粗體顯示，根據表單的字型是。</span><span class="sxs-lookup"><span data-stu-id="d9319-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="d9319-112">請務必呼叫此函式在兩個地方： 在按鈕的<xref:System.Windows.Forms.Control.Click>事件處理常式並在<xref:System.Windows.Forms.Control.FontChanged>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d9319-112">It is important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="d9319-113">如果只有在呼叫此函式<xref:System.Windows.Forms.Control.Click>事件處理常式和其他一些程式碼變更整個表單的字型系列，文字方塊中不會變更表單的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="d9319-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box will not change with the rest of the form.</span></span>  
  
```  
' Visual Basic  
Private Sub MakeBold()  
   ' Change the TextBox to a bold version of the form font  
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
   ' Clicking this button makes the TextBox bold  
   MakeBold()  
End Sub  
  
Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged  
   ' If the TextBox is already bold and the form's font changes,  
   ' change the TextBox to a bold version of the new form font  
   If (TextBox1.Font.Style = FontStyle.Bold) Then  
      MakeBold()  
   End If  
End Sub  
  
// C#  
private void button1_Click(object sender, System.EventArgs e)  
{  
   // Clicking this button makes the TextBox bold  
   MakeBold();  
}  
  
private void MakeBold()   
{  
   // Change the TextBox to a bold version of the form's font  
   textBox1.Font = new Font(this.Font, FontStyle.Bold);  
}  
  
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
   // If the TextBox is already bold and the form's font changes,  
   // change the TextBox to a bold version of the new form font  
   if (textBox1.Font.Style == FontStyle.Bold)   
   {  
      MakeBold();  
   }  
}  
```  
  
 <span data-ttu-id="d9319-114">不過，當當地語系化您的應用程式時，粗體字型可能會顯示特定狀況不佳的語言。</span><span class="sxs-lookup"><span data-stu-id="d9319-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="d9319-115">如果這是一項考量，您會希望當地語系化切換成一般文字的字型從粗體的選項。</span><span class="sxs-lookup"><span data-stu-id="d9319-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="d9319-116">因為當地語系化人員通常不是開發人員，而且不需要存取原始程式碼，只以資源檔，這個選項必須設定資源檔中。</span><span class="sxs-lookup"><span data-stu-id="d9319-116">Since localizers are typically not developers and do not have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="d9319-117">若要這樣做，您會設定<xref:System.Drawing.Font.Bold%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="d9319-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="d9319-118">這樣會寫入至資源檔，當地語系化人員可以編輯的字型設定。</span><span class="sxs-lookup"><span data-stu-id="d9319-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="d9319-119">接著，您撰寫程式碼之後`InitializeComponent`方法來重設字型根據表單的字型，但使用的字型樣式資源檔中指定。</span><span class="sxs-lookup"><span data-stu-id="d9319-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>  
  
```  
' Visual Basic  
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)  
  
// C#  
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9319-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="d9319-120">See Also</span></span>  
 [<span data-ttu-id="d9319-121">全球化 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9319-121">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)  
 [<span data-ttu-id="d9319-122">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="d9319-122">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
