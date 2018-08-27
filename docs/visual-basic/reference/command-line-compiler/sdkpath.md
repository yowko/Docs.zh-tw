---
title: -sdkpath
ms.date: 07/20/2015
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
ms.openlocfilehash: 162c7d58350c381ec667e8a4cd11c03e83fcdf44
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925681"
---
# <a name="-sdkpath"></a>-sdkpath
指定 mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。  
  
## <a name="syntax"></a>語法  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>引數  
 `path`  
 包含 mscorlib.dll 和 Microsoft.VisualBasic.dll 編譯来使用的版本的目錄。 此路徑未驗證之前載入。 將目錄名稱括在引號 ("") 如果它包含空格。  
  
## <a name="remarks"></a>備註  
 此選項會告訴 Visual Basic 編譯器，從非預設位置載入 mscorlib.dll 和 Microsoft.VisualBasic.dll 的檔案。 `-sdkpath`選項設計來搭配[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)。 [!INCLUDE[Compact](~/includes/compact-md.md)]會使用不同版本的支援程式庫，以避免使用的類型和裝置上找不到的語言功能。  
  
> [!NOTE]
>  `-sdkpath`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。 `-sdkpath` Visual Basic 裝置專案載入時，設定選項。  
  
 您可以指定編譯器應使用編譯 Visual Basic 執行階段程式庫參考`-vbruntime`編譯器選項。 如需詳細資訊，請參閱 < [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯`Myfile.vb`具有[!INCLUDE[Compact](~/includes/compact-md.md)]，使用 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的新版的預設安裝目錄中找到[!INCLUDE[Compact](~/includes/compact-md.md)]C 磁碟機上。 一般而言，您會使用最新版本的[!INCLUDE[Compact](~/includes/compact-md.md)]。  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
