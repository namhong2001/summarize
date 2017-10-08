컨테이너를 전부 차지하는 이미지
=======

Image를 그냥 넣으면 화면에 꼭 들어맞게 나오지 않고 이미지 크기 그대로 보인다.
만약 이미지를 상위 container에 꼭 알맞게 또는 화면 가로폭에 꼭 알맞게 보이고자 한다면
다음 방법이 좋다.

    import React, { Component } from 'react';
    import { AppRegistry, ScrollView, Image, Text, StyleSheet, View } from 'react-native';
    
    export default class IScrolledDownAndWhatHappenedNextShockedMe extends Component {
        render() {
            return (
                <ScrollView>
                    <Text style={{fontSize:96}}>Scroll me plz</Text>
                    <FullImage source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Text style={{fontSize:96}}>If you like</Text>
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Text style={{fontSize:96}}>Scrolling down</Text>
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Text style={{fontSize:96}}>What's the best</Text>
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Text style={{fontSize:96}}>Framework around?</Text>
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Image source={require('./img/test.png')} />
                    <Text style={{fontSize:80}}>React Native</Text>
                </ScrollView>
            );
        }
    }
    
    class FullImage extends Component {
        render() {
            return (
                <View style={styles.imageContainer}>
                    <Image style={styles.image} source={this.props.source} />
                </View>
            )
        }
    }
    
    const styles = StyleSheet.create({
        imageContainer: {
            flexDirection: 'row',
            alignItems: 'stretch'
        },
        image:{
            flex: 1
        },
    });
    
## 참고
<https://github.com/facebook/react-native/issues/950>
<https://facebook.github.io/react-native/docs/flexbox.html>
<https://facebook.github.io/react-native/docs/using-a-scrollview.html#content>

