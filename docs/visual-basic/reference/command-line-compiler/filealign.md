---
title: "/filealign |Microsoft 文件"
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
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
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
ms.openlocfilehash: 18d5c3e327e2e41f4786eda6c3e981125f87389d
ms.lasthandoff: 03/13/2017

---
# <a name="filealign"></a>/filealign
指定要對齊輸出檔案區段的位置。  
  
## <a name="syntax"></a>語法  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a>引數  
 `number`  
 必要項。 值，指定輸出檔中區段的對齊方式。 有效值為 512、 1024年、 2048年、 4096、 和 8192。 這些值是以位元組為單位。  
  
## <a name="remarks"></a>備註  
 您可以使用`/filealign`選項指定輸出檔案區段的對齊方式。 包含程式碼或資料的可攜式執行檔 (PE) 檔案中的連續記憶體區塊的區段。 `/filealign`選項可讓您編譯您的應用程式使用標準的對齊方式; 大部分的開發人員不需要使用此選項。  
  
 每個區段對齊的界限時的倍數`/filealign`值。 沒有固定預設值。 如果`/filealign`未指定，編譯器在編譯時期挑選預設值。  
  
 藉由指定區段大小，您可以變更輸出檔的大小。 修改區段大小可能很有用的較小的裝置執行的程式。  
  
> [!NOTE]
>  `/filealign`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
