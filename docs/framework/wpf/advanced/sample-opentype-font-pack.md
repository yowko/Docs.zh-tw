---
title: 範例 OpenType 字型套件
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: 76438b85a12d75efa0fc106a645fb592b3205fad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960976"
---
# <a name="sample-opentype-font-pack"></a>範例 OpenType 字型套件
本主題提供與一起[!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)]散發之範例 OpenType 字型的總覽。 範例字型支援[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式可使用的擴充 OpenType 功能。  

<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>OpenType 字型套件中的字型  
 會提供一組範例 OpenType 字型, 供您用來建立[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式。 [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] 範例字型是根據 Ascender Corporation 的授權來提供。 這些字型只會執行 OpenType 格式所定義的總功能子集。 下表列出範例 OpenType 字型的名稱。  
  
|**名稱**|**檔案**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles Light|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 下圖顯示範例 OpenType 字型的外觀。  
  
 ![列出範例字型套件中的字型名稱](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 範例字型是根據 Ascender Corporation 的授權來提供。 Ascender 是進階字型產品的供應商。 若要授權範例字型的延伸或自訂版本，請參閱 [Ascender Corporation 網站 (英文)](https://go.microsoft.com/fwlink/?LinkId=182627)。  
  
> [!NOTE]
> 身為開發人員，您的職責是確保對於您內嵌在應用程式中或是以其他方式轉散發的任何字型，您必須有必要的授權權限。  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>安裝字型  
 您可以選擇將範例 OpenType 字型安裝到預設的 Windows Fonts 目錄 **\WINDOWS\Fonts**。 使用 [字型] 控制台來安裝字型。 一旦這些字型位於您的電腦上, 所有參考預設 Windows 字型的應用程式都可以存取它們。 您可以按兩下字型檔案，以數個字型大小來顯示一組代表字元。 下列螢幕擷取畫面顯示 Lindsey 字型檔案 Linds.ttf。  
  
 ![Lindsey 字型&#40;OpenType&#41; ](./media/typographyinwpf-04.png "TypographyInWPF_04")  
顯示 Lindsey 字型  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>使用字型  
 有兩種方式可讓您在應用程式中使用字型。 您可將字型新增到您的應用程式以做為專案內容項目，此項目並未內嵌為組件中的資源。 或者，您可以將字型新增到您的應用程式，以做為內嵌於您應用程式組件檔中的專案資源項目。 如需詳細資訊，請參閱[將字型與應用程式一起封裝](packaging-fonts-with-applications.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Documents.Typography>
- [OpenType 字型功能](opentype-font-features.md)
- [將字型與應用程式一起封裝](packaging-fonts-with-applications.md)
