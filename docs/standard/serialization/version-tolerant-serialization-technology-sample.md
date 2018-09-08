---
title: 版本相容序列化技術範例
ms.date: 03/30/2017
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
ms.openlocfilehash: 34dccc9065c0100a01a7969a1fe762001e2999a9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210850"
---
# <a name="version-tolerant-serialization-technology-sample"></a>版本相容序列化技術範例
[下載範例](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 這個範例將示範.NET 序列化的版本相容功能。 此範例會建置使用不同版本之 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 將資料序列化及還原序列化的應用程式。 雖然有不同型別的版本存在，這些應用程式還是能密切地互相通訊。 如需詳細資訊，請參閱[版本相容序列化](../../../docs/standard/serialization/version-tolerant-serialization.md)。  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>若要使用命令提示字元建置範例  
  
1.  開啟 [命令提示字元] 視窗，並巡覽至此範例的任一程式設計語言的子目錄 (V1 Application 或 V2 Application 底下)。  
  
2.  在命令列中輸入 **msbuild.exe \<本> application.sln** (其中 \<本> 為 v1 或 v2)。  
  
### <a name="to-build-the-sample-using-visual-studio"></a>若要使用 Visual Studio 建置範例  
  
1.  開啟 [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]，並巡覽至此範例任一程式設計語言的子目錄。  
  
2.  巡覽至您在前一個步驟選取之目錄的 [V1 Application] 子目錄。  
  
3.  按兩下 V1 Application.sln 的圖示，在 Visual Studio 中開啟檔案。  
  
4.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
5.  巡覽至 [V2 Application] 子目錄，然後重複前兩個步驟，以建置 V2 Application。  
  
 應用程式將建置於其個別專案目錄的預設 \bin 或 \bin\Debug 子目錄中。  
  
### <a name="to-run-the-sample"></a>若要執行範例  
  
1.  在 [命令提示字元] 視窗中，巡覽至您建置範例應用程式時所選的語言特定子目錄。  
  
2.  在命令列輸入 **runme.cmd**，同時執行兩個應用程式。  
  
 或者，巡覽至新可執行檔所在的目錄，然後循序執行這些可執行檔。  
  
> [!NOTE]
>  這個範例會建置一個主控台應用程式。 您必須在 [命令提示字元] 視窗中啟動及執行這些應用程式，才能檢視這些應用程式的輸出。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
- <xref:System.IO.FileStream>
