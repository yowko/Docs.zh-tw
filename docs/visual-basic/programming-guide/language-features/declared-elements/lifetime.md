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
ms.openlocfilehash: 67fe63eecd2aa0c134682708cdeddb21ba06db12
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087488"
---
# <a name="lifetime-in-visual-basic"></a>Visual Basic 中的存留期

宣告專案的 *存留* 期是可供使用的時間週期。 變數是具有存留期的唯一元素。 基於這個目的，編譯器會將程式參數和函數傳回視為變數的特殊案例。 變數的存留期代表可保存值的時間週期。 其值可能會在其存留期內變更，但永遠會保留一些值。  
  
## <a name="different-lifetimes"></a>不同的存留期  

 *成員變數* (在模組層級宣告，而在任何程式之外) 通常與宣告它的元素具有相同的存留期。 在類別或結構中宣告的非共用變數，會以個別的複本形式存在，其為其宣告所在之類別或結構的每個實例。 每個這類變數的存留期都與其實例相同。 不過， `Shared` 變數只會有單一存留期，這會在您的應用程式執行的整個時間持續運作。  
  
 只有在宣告中的程式正在執行時，才會在程式中宣告 (*區域變數*) 存在。 這也適用于該程式的參數和任何函數傳回。 但是，如果該程式呼叫其他程式，則區域變數會在呼叫的程式執行時保留其值。  
  
## <a name="beginning-of-lifetime"></a>存留期開頭  

 本機變數的存留期會在控制項進入其宣告的程式時開始。 一旦程式開始執行，每個區域變數都會初始化為其資料類型的預設值。 當 `Dim` 程式遇到指定初始值的語句時，它會將這些變數設定為這些值，即使您的程式碼已經將其他值指派給它們也是一樣。  
  
 結構變數的每個成員都是以不同的變數來初始化。 同樣地，陣列變數的每個元素都會個別初始化。  
  
 在程式內的區塊中宣告的變數 (例如 `For` 迴圈) 會在進入程式時初始化。 無論您的程式碼是否執行區塊，這些初始化都會生效。  
  
## <a name="end-of-lifetime"></a>存留期結束  

 當程式終止時，不會保留其區域變數的值，Visual Basic 回收其記憶體。 下次當您呼叫程式時，會再次並重新初始化其所有區域變數。  
  
 當類別或結構的實例結束時，其非共用變數會遺失其記憶體和值。 類別或結構的每個新實例都會建立並重新初始化其非共用的變數。 不過， `Shared` 在您的應用程式停止執行之前，會保留變數。  
  
## <a name="extension-of-lifetime"></a>存留期的延伸  

 如果您使用關鍵字宣告本機變數 `Static` ，其存留期會超過其程式的執行時間。 下表顯示程式聲明如何判斷變數存在的時間長度 `Static` 。  
  
|程式位置和共用|靜態變數存留期開始|靜態變數存留期結束|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|在模組 (預設為共用) |第一次呼叫程式時|當您的應用程式停止執行時|  
|在類別中， `Shared` (程式不是實例成員) |第一次在特定實例上或類別或結構名稱本身呼叫程式|當您的應用程式停止執行時|  
|在類別的實例中，not `Shared` (程式是實例成員) |第一次在特定實例上呼叫程式|釋放實例以進行垃圾收集時 (GC) |  
  
## <a name="static-variables-of-the-same-name"></a>相同名稱的靜態變數  

 您可以在多個程式中宣告具有相同名稱的靜態變數。 如果您這麼做，Visual Basic 編譯器會將每個這類變數視為個別的元素。 初始化其中一個變數並不會影響其他變數的值。 如果您定義具有一組多載的程式，並在每個多載中宣告具有相同名稱的靜態變數，則同樣適用。  
  
## <a name="containing-elements-for-static-variables"></a>包含靜態變數的元素  

 您可以在類別內宣告靜態區域變數，也就是在該類別中的程式內。 不過，您不能在結構內宣告靜態區域變數（可以是結構成員），也不能宣告為該結構內之程式的本機變數。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  

 下列範例會宣告具有 [Static](../../../language-reference/modifiers/static.md) 關鍵字的變數。  (請注意， `Dim` 當 [Dim 語句](../../../language-reference/statements/dim-statement.md) 使用的修飾詞（例如）時，您不需要關鍵字 `Static` 。 )   
  
### <a name="code"></a>程式碼  

 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>註解  

 在上述範例中，此變數會在程式 `applesSold` 返回呼叫程式碼之後繼續存在 `runningTotal` 。 下一次 `runningTotal` 呼叫時，會 `applesSold` 保留先前所計算的值。  
  
 如果在未 `applesSold` 使用的情況 `Static` 下宣告，則不會在的呼叫之間保留先前的累積值 `runningTotal` 。 下一次 `runningTotal` 呼叫時， `applesSold` 會重新建立並將它初始化為0，而且 `runningTotal` 只會傳回與其所呼叫的相同值。  
  
### <a name="compile-the-code"></a>編譯程式碼  

 您可以將靜態區域變數的值初始化為其宣告的一部分。 如果您將陣列宣告為 `Static` ，則可以將其排名 () 的維度數目、每個維度的長度，以及個別元素的值。  
  
### <a name="security"></a>安全性  

 在上述範例中，您可以 `applesSold` 在模組層級宣告來產生相同的存留期。 但是，如果您以這種方式變更了變數的範圍，此程式將不再具有其獨佔存取權。 由於其他程式可以存取 `applesSold` 和變更其值，因此執行總數可能不可靠，而且程式碼可能更難維護。  
  
## <a name="see-also"></a>另請參閱

- [共用][](../../../language-reference/modifiers/shared.md)
- [什麼](../../../language-reference/nothing.md)
- [Declared Element Names](declared-element-names.md)
- [References to Declared Elements](references-to-declared-elements.md)
- [Visual Basic 中的範圍](scope.md)
- [Visual Basic 中的存取層級](access-levels.md)
- [變數](../variables/index.md)
- [變數宣告](../variables/variable-declaration.md)
- [疑難排解資料類型的問題](../data-types/troubleshooting-data-types.md)
- [靜態](../../../language-reference/modifiers/static.md)
