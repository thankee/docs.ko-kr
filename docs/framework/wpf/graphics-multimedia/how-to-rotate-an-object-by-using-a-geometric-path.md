---
title: "방법: 기하학적 경로를 사용하여 개체 회전"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 078d1054f9b6a4c2f6172f00aa8c4ad9077e6db2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>방법: 기하학적 경로를 사용하여 개체 회전
이 예제에서 정의 된 기하학적 경로 따라 개체 (피벗)를 회전 하는 방법을 보여 줍니다는 <xref:System.Windows.Media.PathGeometry> 개체입니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 세 개의 <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> 사각형 기하학적 경로 따라 이동 하는 개체입니다.  
  
-   첫 번째 <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> 애니메이션 효과 적용 한 <xref:System.Windows.Media.RotateTransform> 사각형에 적용 되는 합니다. 애니메이션은 각도 값을 생성합니다. 이를 통해 사각형이 경로 윤곽을 따라 회전(피벗)하게 됩니다.  
  
-   다른 두 개의 개체에 애니메이션을 적용는 <xref:System.Windows.Media.TranslateTransform.X%2A> 및 <xref:System.Windows.Media.TranslateTransform.Y%2A> 의 값을 <xref:System.Windows.Media.TranslateTransform> 사각형에 적용 되는 합니다. 이를 통해 사각형이 경로를 따라 가로 및 세로로 이동하게 됩니다.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 기하학적 경로 사용 하 여 개체를 회전 하는 다른 방법은 사용 하는 것을 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> 개체 및 설정의 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> 속성을 `true`합니다. 자세한 내용 및 예제에 대 한 참조 [기하학적 경로 (매트릭스 애니메이션)을 사용 하 여 개체를 회전](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)합니다.  
  
 전체 샘플을 참조 하십시오. [경로 애니메이션 샘플](http://go.microsoft.com/fwlink/?LinkID=160028)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [애니메이션 개요](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [경로 애니메이션 샘플](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [경로 애니메이션 방법 항목](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
