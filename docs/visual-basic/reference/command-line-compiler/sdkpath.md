---
title: -sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53362c2eb5517d9230ea88975745315d6db7f1ba
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-sdkpath"></a>-sdkpath
指定 mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。  
  
## <a name="syntax"></a>語法  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>引數  
 `path`  
 包含 mscorlib.dll 和 Microsoft.VisualBasic.dll 用於編譯的版本的目錄。 未驗證此路徑，直到它載入。 將目錄名稱括在引號 ("") 如果包含空格。  
  
## <a name="remarks"></a>備註  
 此選項會告知[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器，從非預設位置載入 mscorlib.dll 和 Microsoft.VisualBasic.dll 的檔案。 `-sdkpath`選項設計用來搭配[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)。 [!INCLUDE[Compact](~/includes/compact-md.md)]會使用不同版本的支援程式庫，以避免使用的類型和語言功能的裝置上找不到。  
  
> [!NOTE]
>  `-sdkpath`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。 `-sdkpath`時設定選項[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]裝置專案載入。  
  
 您可以指定編譯器應該使用編譯 Visual Basic 執行階段程式庫的參考不`-vbruntime`編譯器選項。 如需詳細資訊，請參閱[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`Myfile.vb`與[!INCLUDE[Compact](~/includes/compact-md.md)]，使用 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本中的預設安裝目錄中找到[!INCLUDE[Compact](~/includes/compact-md.md)]C 磁碟機上。 一般而言，您可使用的最新版本[!INCLUDE[Compact](~/includes/compact-md.md)]。  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
