---
title: "使用規則運算式與 MaskedTextBox 控制項，在 Visual Basic |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 66f61eed8bc8431392d7216ffb799b221489f332
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a><span data-ttu-id="2b106-102">在 Visual Basic 中將規則運算式與 MaskedTextBox 控制項一起搭配使用</span><span class="sxs-lookup"><span data-stu-id="2b106-102">Using Regular Expressions with the MaskedTextBox Control in Visual Basic</span></span>
<span data-ttu-id="2b106-103">這個範例示範如何將簡單的規則運算式，才能使用<xref:System.Windows.Forms.MaskedTextBox>控制項。</xref:System.Windows.Forms.MaskedTextBox></span><span class="sxs-lookup"><span data-stu-id="2b106-103">This example demonstrates how to convert simple regular expressions to work with the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
## <a name="description-of-the-masking-language"></a><span data-ttu-id="2b106-104">遮罩語言說明</span><span class="sxs-lookup"><span data-stu-id="2b106-104">Description of the Masking Language</span></span>  
 <span data-ttu-id="2b106-105">標準<xref:System.Windows.Forms.MaskedTextBox>遮罩語言根據所使用的`Masked Edit`控制[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]6.0 和應該很熟悉來自該平台移轉的使用者。</xref:System.Windows.Forms.MaskedTextBox></span><span class="sxs-lookup"><span data-stu-id="2b106-105">The standard <xref:System.Windows.Forms.MaskedTextBox> masking language is based on the one used by the `Masked Edit` control in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0 and should be familiar to users migrating from that platform.</span></span>  
  
 <span data-ttu-id="2b106-106"><xref:System.Windows.Forms.MaskedTextBox.Mask%2A>屬性<xref:System.Windows.Forms.MaskedTextBox>控制項指定要使用何種輸入的遮罩。</xref:System.Windows.Forms.MaskedTextBox> </xref:System.Windows.Forms.MaskedTextBox.Mask%2A></span><span class="sxs-lookup"><span data-stu-id="2b106-106">The <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property of the <xref:System.Windows.Forms.MaskedTextBox> control specifies what input mask to use.</span></span> <span data-ttu-id="2b106-107">遮罩必須是由一或多個下表中的遮罩項目所組成的字串。</span><span class="sxs-lookup"><span data-stu-id="2b106-107">The mask must be a string composed of one or more of the masking elements from the following table.</span></span>  
  
|<span data-ttu-id="2b106-108">遮罩項目</span><span class="sxs-lookup"><span data-stu-id="2b106-108">Masking element</span></span>|<span data-ttu-id="2b106-109">描述</span><span class="sxs-lookup"><span data-stu-id="2b106-109">Description</span></span>|<span data-ttu-id="2b106-110">規則運算式項目</span><span class="sxs-lookup"><span data-stu-id="2b106-110">Regular expression element</span></span>|  
|---------------------|-----------------|--------------------------------|  
|<span data-ttu-id="2b106-111">0</span><span class="sxs-lookup"><span data-stu-id="2b106-111">0</span></span>|<span data-ttu-id="2b106-112">任何介於 0 到 9 的單一數字。</span><span class="sxs-lookup"><span data-stu-id="2b106-112">Any single digit between 0 and 9.</span></span> <span data-ttu-id="2b106-113">必要項目。</span><span class="sxs-lookup"><span data-stu-id="2b106-113">Entry required.</span></span>|<span data-ttu-id="2b106-114">\d</span><span class="sxs-lookup"><span data-stu-id="2b106-114">\d</span></span>|  
|<span data-ttu-id="2b106-115">9</span><span class="sxs-lookup"><span data-stu-id="2b106-115">9</span></span>|<span data-ttu-id="2b106-116">數字或空格。</span><span class="sxs-lookup"><span data-stu-id="2b106-116">Digit or space.</span></span> <span data-ttu-id="2b106-117">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="2b106-117">Entry optional.</span></span>|<span data-ttu-id="2b106-118">[ \d]?</span><span class="sxs-lookup"><span data-stu-id="2b106-118">[ \d]?</span></span>|  
|#|<span data-ttu-id="2b106-119">數字或空格。</span><span class="sxs-lookup"><span data-stu-id="2b106-119">Digit or space.</span></span> <span data-ttu-id="2b106-120">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="2b106-120">Entry optional.</span></span> <span data-ttu-id="2b106-121">如果這個位置空白遮罩中，它會呈現為空格。</span><span class="sxs-lookup"><span data-stu-id="2b106-121">If this position is left blank in the mask, it will be rendered as a space.</span></span> <span data-ttu-id="2b106-122">加號 （+） 和減號 （-） 允許符號。</span><span class="sxs-lookup"><span data-stu-id="2b106-122">Plus (+) and minus (-) signs are allowed.</span></span>|<span data-ttu-id="2b106-123">[ \d+-]?</span><span class="sxs-lookup"><span data-stu-id="2b106-123">[ \d+-]?</span></span>|  
|<span data-ttu-id="2b106-124">L</span><span class="sxs-lookup"><span data-stu-id="2b106-124">L</span></span>|<span data-ttu-id="2b106-125">ASCII 字母。</span><span class="sxs-lookup"><span data-stu-id="2b106-125">ASCII letter.</span></span> <span data-ttu-id="2b106-126">必要項目。</span><span class="sxs-lookup"><span data-stu-id="2b106-126">Entry required.</span></span>|<span data-ttu-id="2b106-127">[a A-za-z]</span><span class="sxs-lookup"><span data-stu-id="2b106-127">[a-zA-Z]</span></span>|  
|<span data-ttu-id="2b106-128">?</span><span class="sxs-lookup"><span data-stu-id="2b106-128">?</span></span>|<span data-ttu-id="2b106-129">ASCII 字母。</span><span class="sxs-lookup"><span data-stu-id="2b106-129">ASCII letter.</span></span> <span data-ttu-id="2b106-130">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="2b106-130">Entry optional.</span></span>|<span data-ttu-id="2b106-131">[a A-za-z]？</span><span class="sxs-lookup"><span data-stu-id="2b106-131">[a-zA-Z]?</span></span>|  
|&|<span data-ttu-id="2b106-132">字元。</span><span class="sxs-lookup"><span data-stu-id="2b106-132">Character.</span></span> <span data-ttu-id="2b106-133">必要項目。</span><span class="sxs-lookup"><span data-stu-id="2b106-133">Entry required.</span></span>|<span data-ttu-id="2b106-134">[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]</span><span class="sxs-lookup"><span data-stu-id="2b106-134">[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]</span></span>|  
|<span data-ttu-id="2b106-135">C</span><span class="sxs-lookup"><span data-stu-id="2b106-135">C</span></span>|<span data-ttu-id="2b106-136">字元。</span><span class="sxs-lookup"><span data-stu-id="2b106-136">Character.</span></span> <span data-ttu-id="2b106-137">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="2b106-137">Entry optional.</span></span>|<span data-ttu-id="2b106-138">[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]？</span><span class="sxs-lookup"><span data-stu-id="2b106-138">[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?</span></span>|  
|<span data-ttu-id="2b106-139">A</span><span class="sxs-lookup"><span data-stu-id="2b106-139">A</span></span>|<span data-ttu-id="2b106-140">英數字元。</span><span class="sxs-lookup"><span data-stu-id="2b106-140">Alphanumeric.</span></span> <span data-ttu-id="2b106-141">選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="2b106-141">Entry optional.</span></span>|<span data-ttu-id="2b106-142">\W</span><span class="sxs-lookup"><span data-stu-id="2b106-142">\W</span></span>|  
|<span data-ttu-id="2b106-143">.</span><span class="sxs-lookup"><span data-stu-id="2b106-143">.</span></span>|<span data-ttu-id="2b106-144">適當文化特性的小數預留位置。</span><span class="sxs-lookup"><span data-stu-id="2b106-144">Culture-appropriate decimal placeholder.</span></span>|<span data-ttu-id="2b106-145">不適用。</span><span class="sxs-lookup"><span data-stu-id="2b106-145">Not available.</span></span>|  
|<span data-ttu-id="2b106-146">,</span><span class="sxs-lookup"><span data-stu-id="2b106-146">,</span></span>|<span data-ttu-id="2b106-147">文化特性適當的千分位符號。</span><span class="sxs-lookup"><span data-stu-id="2b106-147">Culture-appropriate thousands placeholder.</span></span>|<span data-ttu-id="2b106-148">不適用。</span><span class="sxs-lookup"><span data-stu-id="2b106-148">Not available.</span></span>|  
|<span data-ttu-id="2b106-149">:</span><span class="sxs-lookup"><span data-stu-id="2b106-149">:</span></span>|<span data-ttu-id="2b106-150">適當文化特性的時間分隔符號。</span><span class="sxs-lookup"><span data-stu-id="2b106-150">Culture-appropriate time separator.</span></span>|<span data-ttu-id="2b106-151">不適用。</span><span class="sxs-lookup"><span data-stu-id="2b106-151">Not available.</span></span>|  
|/|<span data-ttu-id="2b106-152">適當文化特性的日期分隔符號。</span><span class="sxs-lookup"><span data-stu-id="2b106-152">Culture-appropriate date separator.</span></span>|<span data-ttu-id="2b106-153">不適用。</span><span class="sxs-lookup"><span data-stu-id="2b106-153">Not available.</span></span>|  
|$|<span data-ttu-id="2b106-154">適當文化特性的貨幣符號。</span><span class="sxs-lookup"><span data-stu-id="2b106-154">Culture-appropriate currency symbol.</span></span>|<span data-ttu-id="2b106-155">不適用。</span><span class="sxs-lookup"><span data-stu-id="2b106-155">Not available.</span></span>|  
|\<|<span data-ttu-id="2b106-156">將轉換成小寫之後的所有字元。</span><span class="sxs-lookup"><span data-stu-id="2b106-156">Converts all characters that follow to lowercase.</span></span>|<span data-ttu-id="2b106-157">不適用。</span><span class="sxs-lookup"><span data-stu-id="2b106-157">Not available.</span></span>|  
|>|<span data-ttu-id="2b106-158">將轉換成大寫之後的所有字元。</span><span class="sxs-lookup"><span data-stu-id="2b106-158">Converts all characters that follow to uppercase.</span></span>|<span data-ttu-id="2b106-159">不適用。</span><span class="sxs-lookup"><span data-stu-id="2b106-159">Not available.</span></span>|  
|<span data-ttu-id="2b106-160">&#124;</span><span class="sxs-lookup"><span data-stu-id="2b106-160">&#124;</span></span>|<span data-ttu-id="2b106-161">設定復原先前的上移或下移。</span><span class="sxs-lookup"><span data-stu-id="2b106-161">Undoes a previous shift up or shift down.</span></span>|<span data-ttu-id="2b106-162">不適用。</span><span class="sxs-lookup"><span data-stu-id="2b106-162">Not available.</span></span>|  
|\|<span data-ttu-id="2b106-163">逸出遮罩字元，將它轉換成常值。</span><span class="sxs-lookup"><span data-stu-id="2b106-163">Escapes a mask character, turning it into a literal.</span></span> <span data-ttu-id="2b106-164">「\\\\」 是一個反斜線逸出序列。</span><span class="sxs-lookup"><span data-stu-id="2b106-164">"\\\\" is the escape sequence for a backslash.</span></span>|\|  
|<span data-ttu-id="2b106-165">所有其他字元。</span><span class="sxs-lookup"><span data-stu-id="2b106-165">All other characters.</span></span>|<span data-ttu-id="2b106-166">常值。</span><span class="sxs-lookup"><span data-stu-id="2b106-166">Literals.</span></span> <span data-ttu-id="2b106-167">所有非遮罩的項目內<xref:System.Windows.Forms.MaskedTextBox>.</xref:System.Windows.Forms.MaskedTextBox> ，就會出現以自身身分</span><span class="sxs-lookup"><span data-stu-id="2b106-167">All non-mask elements will appear as themselves within <xref:System.Windows.Forms.MaskedTextBox>.</span></span>|<span data-ttu-id="2b106-168">所有其他字元。</span><span class="sxs-lookup"><span data-stu-id="2b106-168">All other characters.</span></span>|  
  
 <span data-ttu-id="2b106-169">小數點 （.）、 千分之一 （，）、 時間 （:）、 日期 （/），以及顯示這些符號所定義的應用程式的文化特性的貨幣 （$） 符號預設。</span><span class="sxs-lookup"><span data-stu-id="2b106-169">The decimal (.), thousandths (,), time (:), date (/), and currency ($) symbols default to displaying those symbols as defined by the application's culture.</span></span> <span data-ttu-id="2b106-170">您可以強制它們使用另一個文化特性的符號來顯示<xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>屬性。</xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A></span><span class="sxs-lookup"><span data-stu-id="2b106-170">You can force them to display symbols for another culture by using the <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> property.</span></span>  
  
## <a name="regular-expressions-and-masks"></a><span data-ttu-id="2b106-171">規則運算式與遮罩</span><span class="sxs-lookup"><span data-stu-id="2b106-171">Regular Expressions and Masks</span></span>  
 <span data-ttu-id="2b106-172">雖然您可以使用規則運算式和遮罩來驗證使用者輸入，則不完全相等。</span><span class="sxs-lookup"><span data-stu-id="2b106-172">Although you can use regular expressions and masks to validate user input, they are not completely equivalent.</span></span> <span data-ttu-id="2b106-173">規則運算式可以表達更複雜的模式比遮罩，但遮罩可以表示相同的資訊更簡潔的方式和文化特性所特有的格式。</span><span class="sxs-lookup"><span data-stu-id="2b106-173">Regular expressions can express more complex patterns than masks, but masks can express the same information more succinctly and in a culturally relevant format.</span></span>  
  
 <span data-ttu-id="2b106-174">下表會比較每四個規則運算式和對等的遮罩。</span><span class="sxs-lookup"><span data-stu-id="2b106-174">The following table compares four regular expressions and the equivalent mask for each.</span></span>  
  
|<span data-ttu-id="2b106-175">規則運算式</span><span class="sxs-lookup"><span data-stu-id="2b106-175">Regular Expression</span></span>|<span data-ttu-id="2b106-176">遮罩</span><span class="sxs-lookup"><span data-stu-id="2b106-176">Mask</span></span>|<span data-ttu-id="2b106-177">備註</span><span class="sxs-lookup"><span data-stu-id="2b106-177">Notes</span></span>|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|<span data-ttu-id="2b106-178">`/`遮罩中的字元是邏輯日期分隔符號，，它會顯示給使用者，適用於應用程式的目前文化特性的日期分隔符號。</span><span class="sxs-lookup"><span data-stu-id="2b106-178">The `/` character in the mask is a logical date separator, and it will appear to the user as the date separator appropriate to the application's current culture.</span></span>|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|<span data-ttu-id="2b106-179">中的三個字母月份縮寫顯示第一個字母大寫後面兩個小寫字母與美國格式日期 （日、 月份縮寫和年）。</span><span class="sxs-lookup"><span data-stu-id="2b106-179">A date (day, month abbreviation, and year) in United States format in which the three-letter month abbreviation is displayed with an initial uppercase letter followed by two lowercase letters.</span></span>|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|<span data-ttu-id="2b106-180">選擇性的區碼美國電話號碼。</span><span class="sxs-lookup"><span data-stu-id="2b106-180">United States phone number, area code optional.</span></span> <span data-ttu-id="2b106-181">如果使用者不希望輸入選擇性的字元，她可以輸入空格，或直接將滑鼠指標置於遮罩中的第一個 0 表示的位置。</span><span class="sxs-lookup"><span data-stu-id="2b106-181">If the user does not wish to enter the optional characters, she can either enter spaces or place the mouse pointer directly at the position in the mask represented by the first 0.</span></span>|  
|`$\d{6}.00`|`$999,999.00`|<span data-ttu-id="2b106-182">介於 0 到 999999 貨幣值。</span><span class="sxs-lookup"><span data-stu-id="2b106-182">A currency value in the range of 0 to 999999.</span></span> <span data-ttu-id="2b106-183">貨幣、 千位和十進位字元將會取代在執行階段其特定文化特性的對等用法。</span><span class="sxs-lookup"><span data-stu-id="2b106-183">The currency, thousandth, and decimal characters will be replaced at run-time with their culture-specific equivalents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b106-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b106-184">See Also</span></span>  
 <span data-ttu-id="2b106-185"><xref:System.Windows.Forms.MaskedTextBox.Mask%2A></xref:System.Windows.Forms.MaskedTextBox.Mask%2A></span><span class="sxs-lookup"><span data-stu-id="2b106-185"><xref:System.Windows.Forms.MaskedTextBox.Mask%2A></span></span>   
 <span data-ttu-id="2b106-186"><xref:System.Windows.Forms.MaskedTextBox></xref:System.Windows.Forms.MaskedTextBox></span><span class="sxs-lookup"><span data-stu-id="2b106-186"><xref:System.Windows.Forms.MaskedTextBox></span></span>   
<span data-ttu-id="2b106-187"> [在 Visual Basic 中驗證字串](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md) </span><span class="sxs-lookup"><span data-stu-id="2b106-187"> [Validating Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md) </span></span>  
<span data-ttu-id="2b106-188"> [MaskedTextBox 控制項](http://msdn.microsoft.com/library/235d6121-027d-481d-8d59-4f6794d15d0c)</span><span class="sxs-lookup"><span data-stu-id="2b106-188"> [MaskedTextBox Control](http://msdn.microsoft.com/library/235d6121-027d-481d-8d59-4f6794d15d0c)</span></span>
