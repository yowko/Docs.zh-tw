---
title: -nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d2f3f15ef12b24b8baedc9db59e772aa9eb073bc
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-nowarn"></a>-nowarn
抑制編譯器產生警告的功能。  
  
## <a name="syntax"></a>語法  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`numberList`|選擇性。 編譯器不會顯示警告 ID 編號的逗號分隔清單。 如果未指定警告 Id，則會隱藏所有警告。|  
  
## <a name="remarks"></a>備註  
 `-nowarn`選項讓編譯器將不會產生警告。 若要隱藏個別的警告，提供警告識別碼，`-nowarn`冒號之後的選項。 以逗號分隔多個警告編號。  
  
 您需要指定警告識別項的數字部分。 例如，如果您想要隱藏 BC42024，未使用的區域變數，警告指定`-nowarn:42024`。  
  
 如需有關的警告 ID 編號的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
|在 Visual Studio 整合式的開發環境中設定-nowarn|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.選取**停用所有警告**核取方塊可停都用所有警告。<br />     -或-<br />     若要停用特定警告，請按一下**無**警告相鄰的下拉式清單中。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`並不會顯示任何警告。  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`並不會顯示未使用的區域變數 (42024) 的警告。  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [在 Visual Basic 中設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)
