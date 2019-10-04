---
title: Windows Forms 和控制項中的國際字型
ms.date: 03/30/2017
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
dev_langs:
- csharp
- vb
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
ms.openlocfilehash: 0ddbd6d7a1b614d588a2572b410957a5ed3b768c
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956910"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="9b15e-102">Windows Forms 和控制項中的國際字型</span><span class="sxs-lookup"><span data-stu-id="9b15e-102">International fonts in Windows Forms and controls</span></span>

<span data-ttu-id="9b15e-103">在國際應用程式中，選取字型的建議方法是盡可能使用字體回復。</span><span class="sxs-lookup"><span data-stu-id="9b15e-103">In International applications, the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="9b15e-104">字型回復表示系統會決定該字元所屬的腳本。</span><span class="sxs-lookup"><span data-stu-id="9b15e-104">Font fallback means that the system determines what script the character belongs to.</span></span>

## <a name="using-font-fallback"></a><span data-ttu-id="9b15e-105">使用字型回復</span><span class="sxs-lookup"><span data-stu-id="9b15e-105">Using font fallback</span></span>

<span data-ttu-id="9b15e-106">若要利用這項功能，請不要為您的表單或任何其他元素設定 <xref:System.Drawing.Font> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9b15e-106">To take advantage of this feature, don't set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="9b15e-107">應用程式會自動使用預設系統字型，不同于作業系統的一個當地語系化語言。</span><span class="sxs-lookup"><span data-stu-id="9b15e-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="9b15e-108">當應用程式執行時，系統會自動為作業系統中選取的文化特性提供正確的字型。</span><span class="sxs-lookup"><span data-stu-id="9b15e-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>

<span data-ttu-id="9b15e-109">不設定字型的規則有例外，這是用來變更字型樣式。</span><span class="sxs-lookup"><span data-stu-id="9b15e-109">There's an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="9b15e-110">這對應用程式而言可能很重要，因為使用者按一下按鈕，讓文字方塊中的文字以粗體顯示。</span><span class="sxs-lookup"><span data-stu-id="9b15e-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="9b15e-111">若要這麼做，您可以撰寫函式，根據表單的字型，將文字方塊的字型樣式變更為粗體。</span><span class="sxs-lookup"><span data-stu-id="9b15e-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="9b15e-112">請務必在兩個位置呼叫此函式：在按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式中，以及在 @no__t 1 事件處理常式中。</span><span class="sxs-lookup"><span data-stu-id="9b15e-112">It's important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="9b15e-113">如果只在 <xref:System.Windows.Forms.Control.Click> 事件處理常式中呼叫函式，而其他部分程式碼變更整個表單的字型家族，則文字方塊不會隨著表單的其餘部分而變更。</span><span class="sxs-lookup"><span data-stu-id="9b15e-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box doesn't change with the rest of the form.</span></span>

```vb
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
```

```csharp
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

<span data-ttu-id="9b15e-114">不過，當您將應用程式當地語系化時，粗體字型可能會對某些語言顯示不佳的情況。</span><span class="sxs-lookup"><span data-stu-id="9b15e-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="9b15e-115">如果這是個問題，您希望當地語系化人員可以選擇將字型從粗體切換成一般文字。</span><span class="sxs-lookup"><span data-stu-id="9b15e-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="9b15e-116">由於當地語系化程式通常不是開發人員，而且沒有原始程式碼的存取權，因此，必須在資源檔中設定此選項。</span><span class="sxs-lookup"><span data-stu-id="9b15e-116">Since localizers are typically not developers and don't have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="9b15e-117">若要這樣做，您必須將 <xref:System.Drawing.Font.Bold%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="9b15e-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="9b15e-118">這會導致字型設定寫出到資源檔中，而當地語系化人員可以在其中編輯該檔案。</span><span class="sxs-lookup"><span data-stu-id="9b15e-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="9b15e-119">接著，您可以在 `InitializeComponent` 方法之後撰寫程式碼，以根據表單的字型來重設字型，但使用資源檔中指定的字型樣式。</span><span class="sxs-lookup"><span data-stu-id="9b15e-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a><span data-ttu-id="9b15e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b15e-120">See also</span></span>

- [<span data-ttu-id="9b15e-121">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="9b15e-121">Using Fonts and Text</span></span>](using-fonts-and-text.md)
