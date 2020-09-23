---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: fb317b3c555d151e132122c476ce19bdeceb1321
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065615"
---
# <a name="-main"></a>-main

指定包含 `Sub Main` 程序的類別或模組。  
  
## <a name="syntax"></a>語法  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a>引數  

 `location`  
 必要。 類別或模組的名稱，其中包含 `Sub Main` 程式啟動時所要呼叫的程式。 這可能是下列格式： **module** 或 **-main： namespace. module**。  
  
## <a name="remarks"></a>備註  

 當您建立可執行檔或 Windows 可執行程式時，請使用此選項。 如果省略 **-main** 選項，編譯器會 `Sub Main` 在所有公用類別和模組中搜尋有效的共用。  
  
 如需此程式的各種形式討論，請參閱 [Visual Basic 中的主要](../../programming-guide/program-structure/main-procedure.md) 程式 `Main` 。  
  
 當 `location` 是繼承自的類別時 <xref:System.Windows.Forms.Form> ，編譯器會提供在 `Main` 類別沒有程式時啟動應用程式的預設程式 `Main` 。 這可讓您在開發環境中建立的命令列編譯器代碼。  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>若要在 Visual Studio 整合式開發環境中設定 main  
  
1. 在 **方案總管**中選取專案。 按一下 [專案] 功能表上的 [屬性]。  
  
2. 按一下 [應用程式] **** 索引標籤。  
  
3. 請確定未核取 [ **啟用應用程式架構** ] 核取方塊。  
  
4. 修改 [ **啟始物件** ] 方塊中的值。  
  
## <a name="example"></a>範例  

 下列 `T2.vb` 程式碼會編譯和 `T3.vb` ，並指定在 `Sub Main` 類別中找到程式 `Test2` 。  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [-目標 (Visual Basic) ](target.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [Visual Basic 中的 Main 程序](../../programming-guide/program-structure/main-procedure.md)
