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
ms.openlocfilehash: 85aba17b330af1b25b39f462844bc1a4856a448a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403105"
---
# <a name="-sdkpath"></a>-sdkpath
指定 mscorlib.dll 和 Microsoft 的位置。  
  
## <a name="syntax"></a>語法  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a>引數  
 `path`  
 包含要用於編譯之 mscorlib.dll 和 node.js 版本的目錄。 此路徑要等到載入後才會驗證。 如果目錄名稱包含空格，請將其括在引號（""）中。  
  
## <a name="remarks"></a>備註  
 此選項會告訴 Visual Basic 編譯器從非預設位置載入 mscorlib.dll 和 Microsoft..。 `-sdkpath`選項的設計目的是要搭配[-netcf](netcf.md)使用。 .NET Compact Framework 會使用這些支援程式庫的不同版本，以避免使用在裝置上找不到的類型和語言功能。  
  
> [!NOTE]
> 此 `-sdkpath` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。 `-sdkpath`當載入 Visual Basic 裝置專案時，就會設定此選項。  
  
 您可以指定編譯器在不參考 Visual Basic 執行時間程式庫的情況下，使用 `-vbruntime` 編譯器選項進行編譯。 如需詳細資訊，請參閱[-vbruntime](vbruntime.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會 `Myfile.vb` 使用 .NET Compact Framework 進行編譯，其方式是在 C 磁片磁碟機上 .NET Compact Framework 的預設安裝目錄中找到 mscorlib.dll 和 Microsoft 的版本。 一般來說，您會使用最新版本的 .NET Compact Framework。  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [-netcf](netcf.md)
- [-vbruntime](vbruntime.md)
