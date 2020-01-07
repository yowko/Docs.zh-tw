---
title: 存留期
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: 293537ad33c8e751d49d820fc57ea525e68bc203
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347769"
---
# <a name="lifetime-in-visual-basic"></a>Visual Basic 中的存留期
已宣告專案的*存留*期是可供使用的時間週期。 變數是唯一具有存留期的元素。 基於此目的，編譯器會將程式參數和函數傳回視為變數的特殊情況。 變數的存留期代表它可以保存值的時間週期。 其值可能會在其存留期內變更，但一定會保留一些值。  
  
## <a name="different-lifetimes"></a>不同的存留期  
 *成員變數*（在任何程式之外的模組層級宣告）通常與宣告它的元素具有相同的存留期。 在類別或結構中宣告的非共用變數，會以個別複本的形式存在於其宣告所在的類別或結構的每個實例。 每個這類變數的存留期都與其實例相同。 不過，`Shared` 變數只有單一存留期，這會在應用程式執行的整個時間持續發生。  
  
 *區域變數*（在程式內宣告）只有在宣告它的程式正在執行時，才會存在。 這也適用于該程式的參數和任何函式傳回。 不過，如果該程式呼叫其他程式，則區域變數會在所呼叫的程式正在執行時保留其值。  
  
## <a name="beginning-of-lifetime"></a>存留期的開頭  
 當控制項進入其宣告所在的程式時，就會開始本機變數的存留期。 當程式開始執行時，每個本機變數都會初始化為其資料類型的預設值。 當此程式遇到指定初始值的 `Dim` 語句時，它會將這些變數設定為這些值，即使您的程式碼已將其他值指派給它們也一樣。  
  
 結構變數的每個成員都會初始化為另一個變數。 同樣地，陣列變數的每個元素都會個別初始化。  
  
 在程式內的區塊內宣告的變數（例如 `For` 迴圈）會在程式的進入時初始化。 無論您的程式碼是否執行區塊，這些初始化都會生效。  
  
## <a name="end-of-lifetime"></a>存留期結束  
 當程式終止時，不會保留其區域變數的值，Visual Basic 會回收其記憶體。 下一次呼叫程式時，會再次並重新初始化其所有區域變數。  
  
 當類別或結構的實例終止時，其非共用的變數會遺失其記憶體和其值。 類別或結構的每個新實例會建立並重新初始化其非共用的變數。 不過，在應用程式停止執行之前，會保留 `Shared` 變數。  
  
## <a name="extension-of-lifetime"></a>存留期的延伸  
 如果您使用 `Static` 關鍵字來宣告區域變數，其存留期會超過其程式的執行時間。 下表顯示程式宣告如何判斷 `Static` 變數存在的時間長度。  
  
|程式位置和共用|靜態變數存留期開始|靜態變數存留期結束|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|在模組中（預設為共用）|第一次呼叫程式時|當您的應用程式停止執行時|  
|在類別中，`Shared` （程式不是實例成員）|第一次在特定實例或類別或結構名稱本身上呼叫程式時|當您的應用程式停止執行時|  
|在類別的實例中，不是 `Shared` （程式是實例成員）|第一次在特定實例上呼叫程式時|釋放實例以進行垃圾收集（GC）時|  
  
## <a name="static-variables-of-the-same-name"></a>相同名稱的靜態變數  
 您可以在一個以上的程式中宣告具有相同名稱的靜態變數。 如果您這樣做，Visual Basic 的編譯器會將每個這類變數視為個別的元素。 對其中一個變數進行初始化並不會影響其他變數的值。 如果您定義具有一組多載的程式，並且在每個多載中宣告具有相同名稱的靜態變數，則同樣適用。  
  
## <a name="containing-elements-for-static-variables"></a>包含靜態變數的元素  
 您可以在類別內宣告靜態區域變數，也就是在該類別中的程式內。 不過，您不能在結構中宣告靜態區域變數，其可做為結構成員或該結構內程式的區域變數。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會宣告具有[Static](../../../../visual-basic/language-reference/modifiers/static.md)關鍵字的變數。 （請注意，當[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)使用如 `Static`的修飾詞時，您不需要 `Dim` 關鍵字）。  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>註解  
 在上述範例中，變數 `applesSold` 會在程式 `runningTotal` 回到呼叫程式碼之後繼續存在。 下次呼叫 `runningTotal` 時，`applesSold` 會保留其先前計算的值。  
  
 如果在未使用 `Static`的情況下宣告 `applesSold`，則不會在對 `runningTotal`的呼叫之間保留先前的累積值。 下次呼叫 `runningTotal` 時，`applesSold` 會重新建立並初始化為0，而 `runningTotal` 只會傳回與它所呼叫的相同值。  
  
### <a name="compile-the-code"></a>編譯程式碼  
 您可以初始化靜態區域變數的值，做為其宣告的一部分。 如果您宣告要 `Static`的陣列，您可以初始化它的 rank （維度數目）、每個維度的長度，以及個別元素的值。  
  
### <a name="security"></a>安全性  
 在上述範例中，您可以在模組層級宣告 `applesSold`，以產生相同的存留期。 不過，如果您以這種方式變更變數的範圍，此程式就不會再有獨佔存取權。 因為其他程式可以存取 `applesSold` 並變更其值，所以執行總計可能不可靠，而且程式碼可能更容易維護。  
  
## <a name="see-also"></a>請參閱

- [共用](../../../../visual-basic/language-reference/modifiers/shared.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
