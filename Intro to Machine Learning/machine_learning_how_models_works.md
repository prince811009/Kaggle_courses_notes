# How models work
## Introduction

>We'll start with an overview of how machine learning models work and how they are used. This may feel basic if you've done statistical modeling or machine learning before. Don't worry, we will progress to building powerful models soon.

我們將會先從機器學習模型如何運作以及如何運用的概述開始說起, 如果之前有學過統計建模或是機器學習的人可能會覺得比較基礎, 不過別擔心, 我們將會很快建立起強大的模型.

>This micro-course will have you build models as you go through following scenario:

透過此課程, 可以在完成以下情境時進行建構模型:

>Your cousin has made millions of dollars speculating on real estate. He's offered to become business partners with you because of your interest in data science. He'll supply the money, and you'll supply models that predict how much various houses are worth.

情境為: 你的堂/表兄已經在房地產的預測賺了數百萬美元, 也因為你對 data science 的興趣, 他很願意和你成為商業合作夥伴. 他將提供資金, 而你將提供各種預測房屋價值的模型.

>You ask your cousin how he's predicted real estate values in the past. and he says it is just intuition. But more questioning reveals that he's identified price patterns from houses he has seen in the past, and he uses those patterns to make predictions for new houses he is considering.

你詢問你的堂/表兄他過去如何預測房地產的價值, 但他說這只是他的直覺. 不過更多質疑顯示, 他從過去的房屋中識別出了價格的模式, 接著他利用這些模式對他正在考慮的新房屋做出預測.

>Machine learning works the same way. We'll start with a model called the Decision Tree. There are fancier models that give more accurate predictions. But decision trees are easy to understand, and they are the basic building block for some of the best models in data science.

機器學習的工作方式相同, 我們將從 "決策樹" 的模型開始, 接著會有更高級的模型可以提供更精準的預測, 不過決策樹是容易理解的, 且他們是在 data science 中一些最佳模型的基本建構塊.

>For simplicity, we'll start with the simplest possible decision tree.
簡單起見, 我們將從最簡單的決策樹開始.

![Sample Decision Tree](https://github.com/prince811009/Kaggle_courses_notes/blob/master/imgs/sample_decision_tree.png)

>It divides houses into only two categories. The predicted price for any house under consideration is the historical average price of houses in the same category.

這邊只將房屋分成兩類, 所考慮的任何房屋的預測價格, 為同一類別型態的房屋的歷史平均價格.

>We use data to decide how to break the houses into two groups, and then again to determine the predicted price in each group. This step of capturing patterns from data is called fitting or training the model. The data used to fit the model is called the training data.

我們使用數據來決定如何將房屋分為兩組, 然後再次確定每組中的預測價格。從數據捕獲模式的這一步驟稱為擬合 (fitting) 或訓練模型. 用於擬合模型的數據稱為訓練數據.

>The details of how the model is fit (e.g. how to split up the data) is complex enough that we will save it for later. After the model has been fit, you can apply it to new data to predict prices of additional homes.

有關模型擬合方式的細節, ( 例如如何拆分數據 ) 很複雜, 因此我們稍後再提. 在擬合模型之後, 可以將其應用於新數據以預測其他房屋的價格.

---

## Improving the Decision Tree

>Which of the following two decisions trees is more likely to result from fitting the real estate training data?

以下兩種決策樹中的哪個更有可能是從擬和真實房地產的 training data 產生的呢？

![Improving the Decision Tree-1](https://github.com/prince811009/Kaggle_courses_notes/blob/master/imgs/sample_decision_tree.png)

>The decision tree on the left (Decision Tree 1) probably makes more sense, because it captures the reality that houses with more bedrooms tend to sell at higher prices than houses with fewer bedrooms. The biggest shortcoming of this model is that it doesn't capture most factors affecting home price, like number of bathrooms, lot size, location, etc.

左側的決策樹（Decision Tree 1）可能比較符合, 因為它反映了一個事實, 也就是房間比較多的房屋比房間少的房屋的價格更高, 這種模式最大的缺點為, 它沒有涵蓋大多數影響房價的因素, 例如浴室數量, 地段大小, 位置等.

>You can capture more factors using a tree that has more "splits." These are called "deeper" trees. A decision tree that also considers the total size of each house's lot might look like this:

我們可以利用更多分支的決策樹獲得更多事實, 這些被稱為更深層的樹. 而有考慮到每個房屋總面積的決策樹可能會像這樣:

![Improving the Decision Tree-2](https://github.com/prince811009/Kaggle_courses_notes/blob/master/imgs/sample_decision_tree.png)

>You predict the price of any house by tracing through the decision tree, always picking the path corresponding to that house's characteristics. The predicted price for the house is at the bottom of the tree. The point at the bottom where we make a prediction is called a leaf.

我們可以透過追蹤決策樹來預測任何房屋的價格, 並始終選擇與房屋特徵相對應的路徑, 房屋的預計價格會在樹的底部, 我們在底部進行預測的點稱為枝葉.

>The splits and values at the leaves will be determined by the data, so it's time for you to check out the data you will be working with.

葉子上的拆分和值將由數據確定, 而且現在是換我們檢查要使用的數據了.
