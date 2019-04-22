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
ms.openlocfilehash: 7a8730834c5241ddb1271d689cdda8942741f15f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824919"
---
# <a name="lifetime-in-visual-basic"></a>Visual Basic 中的存留期
*存留期*的宣告的項目是一段時間期間它是可供使用。 變數是其唯一項目具有存留期。 基於此目的，編譯器會將程序參數並函式以傳回特殊的變數。 變數的存留期表示的時間期間中，它可保存的值。 其值可以變更存留期內，但它一律會保留一些值。  
  
## <a name="different-lifetimes"></a>不同的存留期  
 A*成員變數*（在模組層級，任何程序之外宣告） 通常會有相同的存留期，宣告它的項目。 在類別或結構中宣告非共用的變數有以不同的類別或結構宣告它的每個執行個體的複本。 每個這類變數具有相同的存留期，為其執行個體。 不過，`Shared`變數具有只有單一存留期，會在執行您的應用程式的整個期間持續。  
  
 A*區域變數*（程序內宣告） 存在時才會宣告它的程序正在執行。 這也適用於該程序參數與傳回的任何函式。 不過，如果該程序呼叫其他程序，本機變數保留其值時呼叫的程序正在執行。  
  
## <a name="beginning-of-lifetime"></a>存留期的開始  
 當控制項進入其宣告的程序，就會開始本機變數的存留期。 每個本機變數初始化為預設值，其資料類型的程序開始時立即執行。 當此程序遇到`Dim`指定起始值的陳述式，它將這些變數設成這些值，即使您的程式碼必須已指派給它們的其他值。  
  
 結構變數的每個成員都會被視為個別的變數它初始化。 同樣地，會個別初始化陣列變數的每個項目。  
  
 程序內的區塊內宣告的變數 (例如`For`迴圈) 會初始化程序的項目。 無論您的程式碼曾經執行區塊，都會執行初始化。  
  
## <a name="end-of-lifetime"></a>最後的存留期  
 當程序結束時，不會保留其本機變數的值，和 Visual Basic 會回收其記憶體。 下一次呼叫此程序，及其所有區域變數會重新建立，且重新初始化。  
  
 類別或結構的執行個體終止時，其記憶體和它們的值，也將會遺失其非共用的變數。 每個類別或結構的新執行個體建立，並重新初始化其非共用的變數。 不過，`Shared`變數會保留，直到您的應用程式停止執行。  
  
## <a name="extension-of-lifetime"></a>延伸模組的存留期  
 如果您在宣告區域變數`Static`關鍵字，其存留期會超過執行時間，其程序。 下表顯示程序宣告如何決定多久`Static`變數存在。  
  
|程序位置及共用|靜態變數的存留期開始|靜態變數的存留期結束|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|在模組中 （預設為共用）|第一次呼叫程序|當您的應用程式停止執行|  
|在類別中， `Shared` （程序不是執行個體成員）|第一次呼叫程序的特定執行個體或類別或結構名稱本身|當您的應用程式停止執行|  
|類別的執行個體中不`Shared`（程序是執行個體成員）|第一次在特定的執行個體上呼叫程序|執行個體進行記憶體回收 (GC) 的發行時|  
  
## <a name="static-variables-of-the-same-name"></a>具有相同名稱的靜態變數  
 您可以宣告具有相同名稱在一個以上的程序中的靜態變數。 如果您這樣做時，Visual Basic 編譯器會考慮每個這類變數的個別項目。 其中一個變數的初始化不會影響其他的值。 這同樣適用於您定義具有一組多載的程序，並宣告中每個多載相同名稱的靜態變數。  
  
## <a name="containing-elements-for-static-variables"></a>靜態變數的包含項目  
 您可以在該類別中的程序內，也就是宣告在類別中，靜態區域變數。 不過，您無法宣告靜態區域變數結構內，為結構成員，或在該結構中的程序的本機變數。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例宣告的變數[靜態](../../../../visual-basic/language-reference/modifiers/static.md)關鍵字。 (請注意，您不需要`Dim`關鍵字時[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)使用修飾詞，例如`Static`。)  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>註解  
 在上述範例中，變數`applesSold`就會繼續存在的程序之後`runningTotal`傳回給呼叫程式碼。 在下一次`runningTotal`呼叫時，`applesSold`會保留其先前計算的值。  
  
 如果`applesSold`已宣告不用`Static`，不會跨呼叫保留先前的累積的值`runningTotal`。 在下一次`runningTotal`呼叫，則會`applesSold`會重新建立並初始化為 0，及`runningTotal`會直接傳回相同的值與所呼叫。  
  
### <a name="compiling-the-code"></a>編譯程式碼  
 您可以初始化為其宣告的一部分靜態區域變數的值。 如果您宣告為陣列`Static`，您可以初始化其陣序 （維度數目），每個維度的長度，並個別項目的值。  
  
### <a name="security"></a>安全性  
 在上述範例中，您可以產生相同的存留期宣告`applesSold`在模組層級。 如果這種方式變更變數的範圍，不過，程序會不會再有獨佔存取權。 因為其他程序無法存取`applesSold`並變更其值、 加總可能不可靠和程式碼可能是更難維護。  
  
## <a name="see-also"></a>另請參閱

- [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
