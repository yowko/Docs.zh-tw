---
title: "在 Visual Basic 中的為變數進行疑難排解 |Microsoft 文件"
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
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9cddf7ced50c42514ebc9a613f49adee31edde0b
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-variables-in-visual-basic"></a>在 Visual Basic 中為變數進行疑難排解
此頁面會列出使用中的變數時所發生的一些常見問題[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。  
  
## <a name="unable-to-access-members-of-an-object"></a>無法存取物件的成員  
 如果您的程式碼嘗試存取物件的屬性或方法，可能會發生兩種錯誤結果：  
  
-   如果您宣告物件變數屬於特定類型，然後參考該類型未定義的成員，編譯器可能會產生錯誤訊息。  
  
-   執行階段<xref:System.MemberAccessException>指派給物件變數的物件不會公開您的程式碼嘗試存取的成員時，會發生。</xref:System.MemberAccessException> 如果變數是[Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)，您也可以取得此例外狀況，如果成員不是`Public`。 這是因為晚期繫結只允許存取 `Public` 成員。  
  
 當[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)集合型別檢查`On`，只有方法和類別與您將其宣告的屬性，可存取物件變數。 下列範例將說明這點。  

 [!code-vb[VbVbalrVariables #&2;](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]  
  
 在此範例中，`p`可使用的成員<xref:System.Object>類別本身，也不會包含`Left`屬性。</xref:System.Object> 相反地，`q`已宣告型別<xref:System.Windows.Forms.Label>，因此它可以將所有方法和屬性<xref:System.Windows.Forms.Label>類別<xref:System.Windows.Forms>命名空間。</xref:System.Windows.Forms> </xref:System.Windows.Forms.Label> </xref:System.Windows.Forms.Label>  
  
### <a name="correct-approach"></a>正確方法  
 若要能夠存取特定類別之物件的所有成員，請盡可能宣告物件變數屬於該類別的類型。 如果您無法執行此作業，例如，如果您不知道在編譯時期所輸入的物件，您必須設定`Option Strict`至`Off`和宣告的變數[Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)。 這樣就能將任何類型的物件指派給變數，您也應該採取步驟確認目前指派的物件屬於可接受的類型。 您可以使用[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)來做出決定。  
  
## <a name="other-components-cannot-access-your-variable"></a>其他元件無法存取您的變數  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]名稱為*不區分大小寫*。 如果兩個名稱只有字母大小寫不同，則編譯器會將它們解譯成相同的名稱。 例如，它會將 `ABC` 和 `abc` 視為相同的宣告元素。  
  
 不過，Common Language Runtime (CLR) 使用 *區分大小寫* 的繫結。 因此，當您產生一個組件或 DLL 並讓其他組件使用時，您的名稱將會區分大小寫。 例如，如果您使用名為 `ABC`的元素來定義類別，而其他組件透過 Common Language Runtime 使用您的類別，則這些組件必須以 `ABC`來表示該元素。 如果您隨後重新編譯類別，並將元素的名稱變更為 `abc`，則其他使用此類別的組件就無法再存取該元素。 因此，當您發行組件的更新版本時，不應該變更任何公用元素的字母大小寫。  
  
 如需詳細資訊，請參閱[Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482)。  
  
### <a name="correct-approach"></a>正確方法  
 若要讓其他元件能夠存取您的變數，請將其名稱視為區分大小寫。 當您正在測試類別或模組時，請確定其他組件繫結至預定的變數。 一旦發行元件後，請勿修改現有的變數名稱，包括變更其大小寫。  
  
## <a name="wrong-variable-being-used"></a>使用錯誤的變數  
 當您有多個變數具有相同的名稱，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器嘗試解析該名稱的每個參考。 如果變數具有不同的範圍，則編譯器會用最小的範圍來解析宣告的參考。 如果範圍相同，則解析會失敗，且編譯器會發出錯誤信號。 如需詳細資訊，請參閱[宣告之項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
### <a name="correct-approach"></a>正確方法  
 避免使用具有相同名稱但不同範圍的變數。 如果您想要使用其他組件或專案，請盡可能避免使用這些外部元件所定義的任何名稱。 如果您有多個同名的變數時，請務必限定它的每個參考。 如需詳細資訊，請參閱[宣告之項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
## <a name="see-also"></a>另請參閱  
 [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [如何︰ 存取物件的成員](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [如何︰ 決定物件變數參考的類型](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [宣告項目參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
