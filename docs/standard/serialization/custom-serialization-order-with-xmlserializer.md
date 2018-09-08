---
title: 以 XmlSerializer 自訂序列化順序
ms.date: 03/30/2017
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
ms.openlocfilehash: 1dc9a73b45d8e62902ec8c6b7d810154a8a92566
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183323"
---
# <a name="custom-serialization-order-with-xmlserializer"></a>以 XmlSerializer 自訂序列化順序
[下載範例](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 這個範例會示範如何在 XML 序列化中，控制已序列化及已還原序列化之項目的順序。  
  
 如需序列化的詳細資訊，請檢視原始程式碼和 build.proj 檔案中的註解。  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>若要使用命令提示字元建置範例  
  
1.  開啟 [命令提示字元] 視窗，並巡覽至此範例的任一程式設計語言的子目錄。  
  
2.  在命令列鍵入 **msbuild CustomOrder.sln**。  
  
### <a name="to-build-the-sample-using-visual-studio"></a>若要使用 Visual Studio 建置範例  
  
1.  開啟 [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]，並巡覽至此範例任一程式設計語言的子目錄。  
  
2.  按兩下 CustomOrder.sln 的圖示，在 Visual Studio 中開啟這個檔案。  
  
3.  在 [建置] 功能表中，選取 [建置方案]。  
  
4.  此範例應用程式將建置於預設的 \bin 或 \bin\Debug 子目錄中。  
  
## <a name="see-also"></a>另請參閱

- [基本序列化](../../../docs/standard/serialization/basic-serialization.md)  
- [二進位序列化](../../../docs/standard/serialization/binary-serialization.md)  
- [使用屬性控制 XML 序列化](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
- [XML 序列化簡介](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [序列化](../../../docs/standard/serialization/index.md)  
- [XML 和 SOAP 序列化](../../../docs/standard/serialization/xml-and-soap-serialization.md)
