---
title: "在 Visual Basic 中的存留期 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- static variables, lifetime
- static variables, Visual Basic
- declared elements, lifetime
- Shared variable lifetime
- lifetime, declared elements
- lifetime, Visual Basic
- lifetime
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
caps.latest.revision: 14
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fa0cbdf4a8fe5e8fc41e4e4f373c79451fb7b75f
ms.lasthandoff: 03/13/2017

---
# <a name="lifetime-in-visual-basic"></a>Visual Basic 中的存留期
*存留期*的宣告項目是一段時間期間它是可供使用。 變數是唯一的項目存留期。 基於此目的，編譯器會將程序參數和函式會傳回做為變數的特殊案例。 變數的存留期代表一段時間期間，它可以保存的值。 其值會隨著其存留期，而改變，但它永遠會保留某些值。  
  
## <a name="different-lifetimes"></a>不同的存留期  
 A*成員變數*（在模組層級以外的任何程序宣告） 通常會有相同的存留期宣告它的項目。 類別或結構中宣告的非共用的變數存在以不同的類別或結構宣告它的每個執行個體的複本。 每個這類變數具有相同的存留期與其執行個體。 不過，`Shared`變數具有只有單一存留期，可執行應用程式的整個期間持續的時間。  
  
 A*區域變數*（程序內宣告） 宣告它的程序正在執行時才存在。 這也適用於該程序參數與傳回的任何函式。 不過，如果該程序呼叫其他程序，本機變數保留其值在執行時被呼叫的程序。  
  
## <a name="beginning-of-lifetime"></a>存留期的開始  
 本機變數的存留期開始，當控制項進入宣告它的程序。 此程序一開始，將會初始化為其資料類型的預設值的每個本機變數執行。 當程序遇到`Dim`指定起始值的陳述式，它會將設定這些變數初始值，即使您的程式碼有已指定其他值給它們。  
  
 結構變數中的每個成員都會被視為個別的變數它初始化。 同樣地，會分別初始化陣列變數的每個項目。  
  
 在程序內的區塊內宣告的變數 (例如`For`迴圈) 會初始化程序的項目。 無論您的程式碼曾經執行區塊，都會執行初始化。  
  
## <a name="end-of-lifetime"></a>最後的存留期  
 在程序終止時，不會保留其區域變數的值，和[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]回收其記憶體。 下次呼叫程序中，所有的區域變數會從頭建立並重新初始化。  
  
 在類別或結構的執行個體終止時，非共用的變數會遺失其記憶體和它們的值。 每個類別或結構的新執行個體建立，並重新初始化非共用的變數。 不過，`Shared`變數會保留起來，直到您的應用程式停止執行。  
  
## <a name="extension-of-lifetime"></a>延伸模組的存留期  
 如果您宣告的區域變數`Static`關鍵字，其存留期就已經超過其程序的執行時間。 下表顯示程序宣告如何判斷多久`Static`變數存在。  
  
|程序位置及共用|靜態變數的存留期開始|靜態變數的存留期結束|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|在模組中 （預設為共用）|第一次呼叫程序|當您的應用程式停止執行|  
|在類別中， `Shared` （程序不是執行個體成員）|第一次此程序呼叫的特定執行個體或類別或結構的名稱|當您的應用程式停止執行|  
|類別的執行個體中不`Shared`（程序是執行個體成員）|第一次在特定的執行個體呼叫程序|釋放執行個體進行記憶體回收 (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>具有相同名稱的靜態變數  
 您可以宣告具有相同名稱在一個以上的程序中的靜態變數。 如果這樣做，請[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會考慮每個這類變數來個別項目。 其中一個變數的初始化不會影響其他的值。 如果您定義具有一組多載的程序，並套用宣告靜態變數具有相同名稱在每個多載。  
  
## <a name="containing-elements-for-static-variables"></a>靜態變數的包含項目  
 您可以在該類別中的程序內，也就是宣告類別內，靜態區域變數。 不過，您無法宣告結構內，靜態區域變數的結構成員，或在該結構中的程序的本機變數。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 下列範例宣告的變數[靜態](../../../../visual-basic/language-reference/modifiers/static.md)關鍵字。 (請注意，您不需要`Dim`關鍵字時[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)使用修飾詞，例如`Static`。)  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbalrKeywords #&13;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]  
  
### <a name="comments"></a>註解  
 在上述範例中，變數`applesSold`會繼續存在的程序之後`runningTotal`傳回給呼叫程式碼。 在下一次`runningTotal`呼叫時，`applesSold`會保留其先前的導出值。  
  
 如果`applesSold`已宣告不使用`Static`，不會跨呼叫保留先前的累積的值`runningTotal`。 在下一次`runningTotal`已呼叫`applesSold`會重新建立並初始化為 0，和`runningTotal`會直接傳回相同的值與被呼叫。  
  
### <a name="compiling-the-code"></a>編譯程式碼  
 您可以初始化靜態區域變數做為其宣告的一部分的值。 如果您宣告為陣列`Static`，您可以初始化其陣序規範 （維度數目）、 每個維度，以及個別項目的值。  
  
### <a name="security"></a>安全性  
 在上述範例中，您可以產生相同的存留期宣告`applesSold`在模組層級。 如果這種方式變更變數的範圍，不過，程序就不再需要獨佔存取。 因為其他程序無法存取`applesSold`並變更其值、 加總可能不可靠和程式碼可能會更難維護。  
  
## <a name="see-also"></a>另請參閱  
 [共用](../../../../visual-basic/language-reference/modifiers/shared.md)   
 [執行任何動作](../../../../visual-basic/language-reference/nothing.md)   
 [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [宣告項目參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)
