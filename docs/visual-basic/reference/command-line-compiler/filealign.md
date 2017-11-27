---
title: /filealign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbabc19c85501b97ef5443a6f6e12524f8de7d91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="filealign"></a>/filealign
指定要對齊輸出檔案區段的位置。  
  
## <a name="syntax"></a>語法  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a>引數  
 `number`  
 必要項。 值，指定輸出檔案區段的對齊方式。 有效值為 512、1024、2048、4096 和 8192。 這些值是以位元組為單位。  
  
## <a name="remarks"></a>備註  
 您可以使用`/filealign`選項來指定輸出檔案區段的對齊方式。 區段是包含程式碼或資料的可攜式執行檔 (PE) 檔案中的連續記憶體區塊。 `/filealign`選項可讓您編譯您的應用程式與標準的對齊方式; 大部分的開發人員不需要使用這個選項。  
  
 每個區段對齊的倍數界限`/filealign`值。 沒有固定預設值。 如果`/filealign`未指定，則編譯器會在編譯時期挑選預設值。  
  
 藉由指定區段大小，您可以變更輸出檔的大小。 修改區段大小對執行於較小裝置上的程式而言可能很有用。  
  
> [!NOTE]
>  `/filealign`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
