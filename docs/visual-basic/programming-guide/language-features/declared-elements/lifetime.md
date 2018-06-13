---
title: Visual Basic 中的存留期
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
ms.openlocfilehash: d32639f1c392d53a7e9f6258440b6c0925d27a5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654225"
---
# <a name="lifetime-in-visual-basic"></a>Visual Basic 中的存留期
*存留期*的宣告的項目是一段時間期間它是可供使用。 變數是唯一的項目存留期的。 基於此目的，編譯器會將程序參數和函式會傳回做為變數的特殊案例。 變數的存留期代表一段時間期間中，它能容納的值。 其值可以變更其存留期，但它永遠會保留一些值。  
  
## <a name="different-lifetimes"></a>不同的存留期  
 A*成員變數*（在模組層級，任何程序之外宣告） 通常會有相同的存留期宣告它的項目。 在類別或結構中宣告非共用的變數存在以不同的類別或結構宣告它的每個執行個體的複本。 每個這類變數都有相同的存留期為其執行個體。 不過，`Shared`變數具有只有單一存留期，可執行應用程式的整個期間持續。  
  
 A*區域變數*（程序內宣告） 只在宣告它的程序正在執行時，才會存在。 這也適用於該程序的參數與傳回的任何函式。 不過，如果該程序呼叫其他程序，本機變數保留其值在執行時呼叫的程序。  
  
## <a name="beginning-of-lifetime"></a>存留期的開始  
 當控制項進入宣告它的程序時，就會開始本機變數的存留期。 每個本機變數初始化為其資料類型的預設值為程序開始執行。 當程序遇到`Dim`指定起始值的陳述式，將這些變數設這些值，即使您的程式碼已有指派給他們的其他值。  
  
 結構變數的每個成員都會被視為個別的變數它初始化。 同樣地，會個別初始化陣列變數的每個項目。  
  
 在程序內的區塊內宣告的變數 (例如`For`迴圈) 的程序項目就會初始化。 不論您的程式碼執行區塊，都會執行初始化。  
  
## <a name="end-of-lifetime"></a>存留期即將結束  
 當程序終止時，不會保留其區域變數的值，和 Visual Basic 會回收記憶體。 下次呼叫程序中，所有的區域變數是從頭建立且重新初始化。  
  
 當類別或結構的執行個體終止時，非共用的變數會遺失其記憶體和其值。 每個類別或結構的新執行個體建立，並重新初始化非共用的變數。 不過，`Shared`變數會保留起來，直到您的應用程式停止執行。  
  
## <a name="extension-of-lifetime"></a>延伸模組的存留期  
 如果您宣告的區域變數`Static`關鍵字，其存留期的長度超過其程序執行時間。 下表顯示程序宣告如何決定多久`Static`變數存在。  
  
|程序位置及共用|靜態變數的存留期開始|靜態變數的存留期結束|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|在模組中 （預設為共用）|第一次呼叫程序|當您的應用程式停止執行|  
|在類別中， `Shared` （程序不是執行個體成員）|第一次程序呼叫的特定執行個體或類別或結構的名稱|當您的應用程式停止執行|  
|類別的執行個體中不`Shared`（程序是執行個體成員）|第一次在特定的執行個體呼叫程序|釋放執行個體進行記憶體回收 (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>具有相同名稱的靜態變數  
 您可以宣告具有相同名稱在一個以上的程序中的靜態變數。 如果您這麼做時，Visual Basic 編譯器會考慮每個這類變數來個別項目。 其中一個變數的初始化不會影響其他的值。 如果您定義一組多載的程序，並宣告中每個多載相同名稱的靜態變數，套用相同。  
  
## <a name="containing-elements-for-static-variables"></a>靜態變數的包含項目  
 您可以在該類別中的程序內，也就是宣告類別內，靜態區域變數。 不過，您無法宣告靜態區域變數結構內，是為結構成員或在該結構中的程序的本機變數。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例宣告的變數[靜態](../../../../visual-basic/language-reference/modifiers/static.md)關鍵字。 (請注意，您不需要`Dim`關鍵字時[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)使用修飾詞，例如`Static`。)  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbalrKeywords#13](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]  
  
### <a name="comments"></a>註解  
 在上述範例中，變數`applesSold`仍然存在於程序之後`runningTotal`傳回給呼叫程式碼。 在下一次`runningTotal`呼叫時，`applesSold`保留其先前導出的值。  
  
 如果`applesSold`而不使用已宣告項目`Static`，先前的累積的值不會保留在對呼叫之間`runningTotal`。 在下一次`runningTotal`已呼叫`applesSold`會重新建立並初始化為 0，和`runningTotal`會都只會傳回相同的值與呼叫它。  
  
### <a name="compiling-the-code"></a>編譯程式碼  
 您可以初始化靜態區域變數做為其宣告的一部分的值。 如果您宣告為陣列`Static`，您可以初始化其陣序 （維度數目），每個維度的長度，並個別項目的值。  
  
### <a name="security"></a>安全性  
 在上述範例中，您可以產生相同的存留期宣告`applesSold`在模組層級。 如果這種方式變更變數的範圍，不過，程序就不再需要獨佔存取權。 因為其他程序無法存取`applesSold`並變更其值加總可能不可靠，程式碼可能是更難維護。  
  
## <a name="see-also"></a>另請參閱  
 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)
