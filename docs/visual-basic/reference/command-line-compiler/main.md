---
title: -主要
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: e1e636da1d277f80f58268b24b69802006eb8315
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966277"
---
# <a name="-main"></a>-主要
指定包含 `Sub Main` 程序的類別或模組。  
  
## <a name="syntax"></a>語法  
  
```  
-main:location  
```  
  
## <a name="arguments"></a>引數  
 `location`  
 必要項。 名稱的類別或模組，其中包含`Sub Main`程式啟動時要呼叫的程序。 這可能是在表單 **-主要： module**或是 **-main:namespace.module**。  
  
## <a name="remarks"></a>備註  
 當您建立可執行檔或 Windows 可執行程式時，請使用此選項。 如果 **-主要**略過選項，編譯器會搜尋有效的共用`Sub Main`所有公用類別和模組中。  
  
 請參閱[在 Visual Basic 中的 Main 程序](../../../visual-basic/programming-guide/program-structure/main-procedure.md)的各種形式的討論`Main`程序。  
  
 當`location`是一個類別，繼承自<xref:System.Windows.Forms.Form>，編譯器會提供預設值`Main`程序，啟動應用程式，如果類別沒有`Main`程序。 這可讓您在命令列建立開發環境中的程式碼編譯。  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>若要設定-主要 Visual Studio 整合式的開發環境  
  
1.  在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。  
  
2.  按一下 [應用程式]  索引標籤。  
  
3.  請確定**啟用應用程式架構**未核取核取方塊。  
  
4.  修改中的值**啟始物件** 方塊中。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯`T2.vb`並`T3.vb`，並指定可`Sub Main`程序就會出現在`Test2`類別。  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [在 Visual Basic 中的 main 程序](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
