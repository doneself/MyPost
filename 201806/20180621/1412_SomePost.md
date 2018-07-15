# Airbnb 宣布放弃使用 React Native，回归使用原生技术

[![局长](https://static.oschina.net/uploads/user/1360/2720166_50.jpg?t=1470892376000)](https://my.oschina.net/hardbone) [局长](https://my.oschina.net/hardbone) 发布于2018年06月21日 收藏 7

[![img](https://static.oschina.net/uploads/space/2018/0620/105155_sj38_2663968.jpg)](http://clickc.admaster.com.cn/c/a109734,b2619654,c3159,i0,m101,8a1,8b2,h)

[![React Native](https://static.oschina.net/uploads/logo/reactnative_GOL2Q.png)](https://www.oschina.net/p/reactnative)

![img](https://oscimg.oschina.net/oscnet/e7eb89028320a0967466dc4c494ea1111a2.jpg)

> 昨日，Airbnb 技术团队在 Medium 上[宣布](https://medium.com/airbnb-engineering/sunsetting-react-native-1868ba28e30a)，Airbnb 放弃使用 React Native，将回归到使用基于原生技术的自有框架开发 App。

Airbnb 表示，尽管很多团队都依赖 React Native 并计划在可预见的将来使用它，但他们最终还是无法实现最初的目标。此外，还有一些他们无法克服的[技术](https://medium.com/airbnb-engineering/react-native-at-airbnb-the-technology-dafd0b43838)和[组织](https://medium.com/airbnb-engineering/building-a-cross-platform-mobile-team-3e1837b40a88)挑战，如果继续使用 React Native，这些挑战最终会变成更大的难题。

因此，Airbnb 宣布放弃使用 React Native，并将所有的努力重新投入到基于原生技术开发 App。

Airbnb 在博客中提到，当 React Native 按照预期运行时，工程师能以惊人的速度开发应用。然而实际情况是由于众多的技术和组织问题，RN 反而给项目带来了意外的延迟，还增加了项目成员的挫败感。

接着，Airbnb 表示尽管 React Native 中的代码几乎完全是跨平台共享的，但他们的应用程序中只有一小部分是 React Native。另外还需要编写大量桥接基础设施的代码，以保证产品工程师能够有效地工作。因此，他们最后是在三个平台（React Native, Android, iOS），而不是两个平台上进行编码。

可以看到，Airbnb 放弃使用 React Native 的主要原因是 React Native 未能实现完全的跨平台抽象，有时候仍然需要针对特定平台单独编写代码来解决问题。这就间接要求他们的工程师必须熟悉三个平台才能真正用好 React Native，然而绝大多数开发者只熟悉一两个平台，久而久之便引发了一系列的问题。

最后，Airbnb 说道，决定是否使用新平台是一个重大决定，这完全取决于你团队独有的因素。他们的经历和放弃原因可能不适用于你的团队。事实上，[许多](https://medium.com/@Pinterest_Engineering/supporting-react-native-at-pinterest-f8c2233f90e6)[公司](https://instagram-engineering.com/react-native-at-instagram-dd828a9a90c7)今天仍在继续使用 React Native，它可能仍然是许多其他公司的最佳选择。

相关链接

- React Native 的详细介绍：[点击查看](https://www.oschina.net/p/reactnative)
- React Native 的下载地址：[点击下载](https://www.oschina.net/home/login?goto_page=https%3A%2F%2Fwww.oschina.net%2Fnews%2F97276%2Fairbnb-sunsetting-react-native)

###    