.. _getting-started:

Getting Started with React Native
=================================

Based on the complete React Native and Redux class on Udemy

Step1: install all dependencies
-------------------------------

.. image:: ../img/gs-native/nt1.png

1.1 Install Xcode

1.2 Install Homebew -> brew.sh

.. code::

        $ /usr/bin/ruby -e "$(curl -fsSL
        https://raw.githubusercontent.com/Homebrew/install/master/install)"
        $ brew update

3. Install Node/NPM

.. code::

      $ brew install node
      $ node -v

4. Install watchman : to watch our hard drive for file changes

.. code::

      $ brew install watchman

5. Install RN CLI

.. code::

      $ npm install -g react-native-cli

------------

Step2: create your first react-native project
---------------------------------------------

.. code::

        $ react-native init albums
        $ cd albums
        $ react-native run-ios

.. image:: ../img/gs-native/nt2.png

Step3: make changes to your project
-----------------------------------

1. Download WebStorm or Atom IDE

   https://www.jetbrains.com/webstorm/download/

   https://atom.io

------------

2. Install and configure ‘ESLint’ for IDE (for code quality check)

2.1 WebStorm, then add Flow to Language & Framework

    https://blog.jetbrains.com/webstorm/2016/11/using-flow-in-webstorm/

2.2 Atom

.. image:: ../img/gs-native/nt3.png

.. image:: ../img/gs-native/nt4.png

.. image:: ../img/gs-native/nt5.png

go inside your project, then in terminal type the following to install npm module

.. code::

        albums$ npm install --save-dev eslint-config-rallycoding

then create a ‘.eslintrc’ file under ‘root’ folder

.. image:: ../img/gs-native/nt6.png

------------

3. Open project folder, you will see the following screen

.. image:: ../img/gs-native/nt7.png

!!! side note : differences between ‘React’ and ‘React Native’

.. image:: ../img/gs-native/nt8.png

!!! side note: components in ‘React’ and ‘React-Native’ is generated using JSX

!!! side note: use ‘Babel’ a tool to turn ‘JSX’ into normal ‘javascript’

.. image:: ../img/gs-native/nt9.png

------------

4. inside ‘index.ios.js’ let’s get started

.. code::

          //index.ios.js place code in here for iOS

          //Import a library to help create a Component
          import React from ‘react’;
          import { Text, AppRegistry } from ‘react-native’;

          //create a Component
          const App = () => (
          <Text>Something</Text>
          );

          //Render it to the device
          AppRegistry.registerComponent(‘test2’, () => App);

.. image:: ../img/gs-native/nt10.png

------------

Step4: Application Outline
-----------------------------------

.. image:: ../img/gs-native/nt11.png

Step5: Create Header Component
-----------------------------------

.. image:: ../img/gs-native/nt12.png

1. create file header.js inside albums/src/components

.. image:: ../img/gs-native/nt13.png

.. code:: Python

        //path> src/components/header.js
        //Import a library to help create a Component
        import React from 'react';
        import { Text } from 'react-native';

        //create a Component
        const Header = () => {
            return <Text>Albums!</Text>
        };

        //Make the component available to other parts of the app
        export default Header;

2. make change to ‘index.ios.js’

.. code:: Python

      //index.ios.js place code in here for iOS
      //Import a library to help create a Component
      import React from ‘react’;
      import { AppRegistry } from ‘react-native’;
      import Header from ‘./src/components/header’;

      //create a Component
      const App = () => (
      <Header />
      );

      //Render it to the device
      AppRegistry.registerComponent(‘albums’, () => App);

3. Then refresh ios simulator

4. style the header

.. code:: Python

      //path> src/components/header.js
      //Import a library to help create a Component
      import React from ‘react’;
      import { Text } from ‘react-native’;

      //create a Component
      const Header = () => {
        const { textStyle } = styles;
          return <Text style = {textStyle}>Albums!</Text>
      };

      const styles = {
        textStyle: {
        fontSize: 20
        }
      };

      //Make the component available to other parts of the app
      export default Header;

.. image:: ../img/gs-native/nt14.png

5. style more components

.. image:: ../img/gs-native/nt15.png

.. code::
        //path> src/components/header.js
        //Import a library to help create a Component
        import React from ‘react’;
        import { Text, View } from ‘react-native’;

        //create a Component
        const Header = () => {
          const { textStyle, viewStyle } = styles;
          return (
          <View style = {viewStyle}>
          <Text style = {textStyle}>Albums!</Text>
          </View>
          );
        };

        const styles = {
          viewStyle: {
          backgroundColor: ‘#CECBCB’
          },
          textStyle: {
          fontSize: 20
          }
        };

        //Make the component available to other parts of the app
        export default Header;

.. image:: ../img/gs-native/nt15.png

6. introduction to ‘flexbox’

- justifyItems (vertical): ‘flex-start’, ‘center’, ‘flex-end’

- alignItems (horizontal): ‘flex-start’, ‘center’, ‘flex-end’

.. image:: ../img/gs-native/nt16.png

.. image:: ../img/gs-native/nt17.png

.. image:: ../img/gs-native/nt18.png

.. image:: ../img/gs-native/nt19.png

.. image:: ../img/gs-native/nt20.png

.. image:: ../img/gs-native/nt21.png

.. image:: ../img/gs-native/nt22.png


.. code::
        //path> src/components/header.js
        //Import a library to help create a Component
        import React from ‘react’;
        import { Text, View } from ‘react-native’;

        //create a Component
        const Header = () => {
          const { textStyle, viewStyle } = styles;
          return (
          <View style = {viewStyle}>
          <Text style = {textStyle}>Albums!</Text>
          </View>
         );
        };

        const styles = {
          viewStyle: {
          backgroundColor: ‘#F8F8F8s’,
          justifyContent: ‘center’,
          alignItems: ‘center’,
          height: 60,
          paddingTop: 15,
          shadowColor: ‘#000’,
          shadowOffset: {width:0, height: 2},
          shadowOpacity: 0.2
          },
          textStyle: {
          fontSize: 20
          }
        };

        //Make the component available to other parts of the app
        export default Header;

.. image:: ../img/gs-native/nt23.png

7. making header reusable

.. image:: ../img/gs-native/nt24.png

.. image:: ../img/gs-native/nt25.png

------------

Step6: HTTP Requests with React Native
--------------------------------------

1. Idea

.. image:: ../img/gs-native/nt26.png

.. image:: ../img/gs-native/nt27.png

2. add ‘AlbumList.js’ under ‘src/components/’

.. image:: ../img/gs-native/nt28.png

.. image:: ../img/gs-native/nt29.png

3. create class based components (becase we want to handle data from http request)

in this step we refactor ‘AlbumList.js’ from functional component to class-based component

.. image:: ../img/gs-native/nt30.png

.. image:: ../img/gs-native/nt31.png

4. Life-cycle method : how to debug the application

- edit ‘AlbumList.js’ to include code to for debugging log

.. image:: ../img/gs-native/nt32.png

- click ‘command + D’ you will see below screen and the debugger screen pops up, then click ‘debug JS remotely’

.. image:: ../img/gs-native/nt33.png

.. image:: ../img/gs-native/nt34.png

when we put ‘debugger;’ in the code it will run app in debug mode and stop where you put the code

.. image:: ../img/gs-native/nt35.png

.. image:: ../img/gs-native/nt36.png

5. Network Requests : make a http ‘get’ request to the backend to get data objects

.. image:: ../img/gs-native/nt37.png

.. image:: ../img/gs-native/nt38.png

here’s what has happened

.. image:: ../img/gs-native/nt39.png

the big issue is sometimes the page gets rendered faster than when the data came, we need to fix this issue by using ‘Component State Level’ to wait for returned data that will get rendered again

6. Component Level State

.. image:: ../img/gs-native/nt40.png

.. image:: ../img/gs-native/nt41.png

.. image:: ../img/gs-native/nt42.png

we sees that the page gets rendered 2 time with the 1st ‘albums’ array with 0 objects but 2nd ‘albums’ array with 5 objects

here is the api to get sample ‘json’ data > http://rallycoding.herokuapp.com/api/music_albums

7. more on ‘Component Level State’

.. image:: ../img/gs-native/nt43.png

.. image:: ../img/gs-native/nt44.png

8. Rendering a list of components

.. image:: ../img/gs-native/nt45.png

.. image:: ../img/gs-native/nt46.png

.. image:: ../img/gs-native/nt47.png

9. Displaying individual albums: refactor code so that we can separate AlbumDetail

.. image:: ../img/gs-native/nt48.png

.. image:: ../img/gs-native/nt49.png

.. code::

        //path> src/components/AlbumList.js
        import React, { Component } from ‘react’;
        import { Text, View } from ‘react-native’;
        import axios from ‘axios’;
        import AlbumDetail from ‘./AlbumDetail’;

        //create class here
        class AlbumList extends Component {
          state = {albums: []}; //set empty state

        componentWillMount(){
          console.log(‘componentWillMount in AlbumList’);
          axios.get(‘https://rallycoding.herokuapp.com/api/music_albums')
          .then(response => this.setState({albums: response.data}));
          //setState will help rerendering this page when new data come
        }

        renderAlbums() {
          return this.state.albums.map(album => <AlbumDetail key={album.title} album={album} />);
        }

        render() {
          console.log(this.state);
          return(
          <View>
          {this.renderAlbums()}
          </View>
          );
          }
        }

        export default AlbumList;

10. fantastic reusable components — the card

- here is our game plan

.. image:: ../img/gs-native/nt50.png

.. image:: ../img/gs-native/nt51.png

*withour reusable components*

.. image:: ../img/gs-native/nt52.png

*alternative layout with reusable components*

.. code::

        //path> src/components/Card.js
        import React, { Component } from ‘react’;
        import { Text, View } from ‘react-native’;

        //create functional component here
        const Card = () => {
          return(
           <View>

        </View>
         );
        };

        export default Card;

11. styling card

.. code::

            //path> src/components/Card.js
            import React, { Component } from ‘react’;
            import { Text, View } from ‘react-native’;

            //create functional component here
            const Card = () => {
              return(
              <View style={styles.ContainerStyle}>

            </View>
              );
            };

            const styles = {
              ContainerStyle: {
              borderWidth: 1,
              borderRadius: 2,
              borderColor: ‘#ddd’,
              borderBottomWidth: 0,
              shadowColor: ‘#000’,
              shadowOffset: {width: 0, height: 2},
              shadowOpacity: 0.1,
              shadowRadius: 2,
              elevation: 1,
              marginLeft: 5,
              marginRight: 5,
              marginTop: 10
              },

            }

12. passing components as props

.. code::

            //path> src/components/Card.js
            import React, { Component } from ‘react’;
            import { Text, View } from ‘react-native’;

            //create functional component here
            const Card = (props) => {
              return(
              <View style={styles.ContainerStyle}>
              {props.children}
              </View>
              );
            };

            const styles = {
              ContainerStyle: {
              borderWidth: 1,
              borderRadius: 2,
              borderColor: ‘#ddd’,
              borderBottomWidth: 0,
              shadowColor: ‘#000’,
              shadowOffset: {width: 0, height: 2},
              shadowOpacity: 0.1,
              shadowRadius: 2,
              elevation: 1,
              marginLeft: 5,
              marginRight: 5,
              marginTop: 10
              },

            }

            export default Card;

then make change to AlbumDetail.js

.. code::

            //path> src/components/AlbumDetail.js
            import React, { Component } from ‘react’;
            import { Text, View } from ‘react-native’;
            import Card from ‘./Card’

            //create functional component here
            const AlbumDetail = (props) => {
              return(
              <Card>
              <Text>{props.album.title}</Text>
              </Card>
              );
            };

            export default AlbumDetail;

.. image:: ../img/gs-native/nt53.png

13. dividing cards into sections

.. image:: ../img/gs-native/nt54.png

.. image:: ../img/gs-native/nt55.png

------------

Step7: Handling Component Layout
________________________________

7.1 mastering layout with flexbox

.. image:: ../img/gs-native/nt56.png

*Here is what we want*

.. image:: ../img/gs-native/nt57.png

*if we ignore styling*

.. image:: ../img/gs-native/nt58.png

*we can do justifyContent*

.. image:: ../img/gs-native/nt59.png

.. image:: ../img/gs-native/nt60.png

7.2 positioning of elements on mobile

.. image:: ../img/gs-native/nt72-1.png

*here’s what we have to do*

.. image:: ../img/gs-native/nt72-2.png

.. image:: ../img/gs-native/nt72-3.png

.. image:: ../img/gs-native/nt72-4.png

7.3 more on styling

.. image:: ../img/gs-native/nt73-1.png

.. image:: ../img/gs-native/nt73-2.png

7.4 images with React Native

..code ::

          //path> src/components/AlbumDetail.js
          import React from 'react';
          import { Text, View, Image } from 'react-native';
          import Card from './Card'
          import CardSection from './CardSection'

          //create functional component here
          const AlbumDetail = ({ album }) => {
            const { title, artist, thumbnail_image } = album;
            const { thumbnailStyle, headerContentStyle } = styles;

          return (
            <Card>
              <CardSection>
              <View>
                <Image
                  style={thumbnailStyle}

                />
              </View>
              <View style={headerContentStyle}>
                <Text>{title}</Text>
                <Text>{artist}</Text>
              </View>
              </CardSection>
            </Card>
            );
          };

          const styles = {
            headerContentStyle: {
              flexDirection: 'column',
              justifyContent: 'space-around'
            },
            thumbnailStyle: {
              height: 50,
              width: 50
              }
          };

          export default AlbumDetail;

.. image:: ../img/gs-native/nt74-1.png

7.5 displaying album artwork

.. code::

          //path> src/components/AlbumDetail.js
          import React from 'react';
          import { Text, View, Image } from 'react-native';
          import Card from './Card'
          import CardSection from './CardSection'

          //create functional component here
          const AlbumDetail = ({ album }) => {
            const { title, artist, thumbnail_image, image } = album;
            const { thumbnailStyle, headerContentStyle,
          thumbnailContainerStyle,
            headerTextStyle, imageStyle } = styles;

          return (
            <Card>
              // header section
              <CardSection>
              <View style={thumbnailContainerStyle}>
                <Image
                  style={thumbnailStyle}

                />
              </View>
              <View style={headerContentStyle}>
                <Text style={headerTextStyle}>{title}</Text>
                <Text>{artist}</Text>
              </View>
              </CardSection>
              // image section
              <CardSection>
                <Image
                  style={imageStyle}

                />
              </CardSection>
             </Card>
            );
          };

          const styles = {
            headerContentStyle: {
              flexDirection: 'column',
              justifyContent: 'space-around'
            },
            headerTextStyle: {
              fontSize: 18
              },
            thumbnailStyle: {
              height: 50,
              width: 50
            },
            imageStyle: {
              height: 300,
              flex: 1,
              width: null
            },
            thumbnailContainerStyle: {
              justifyContent: 'center',
              alignItems: 'center',
              marginLeft: 10,
              marginRight: 10
            }
          };

          export default AlbumDetail;

.. image:: ../img/gs-native/nt75-1.png

.. image:: ../img/gs-native/nt75-2.png

7.6 making content scrollable

step1: select which part of the app is scrollable

.. image:: ../img/gs-native/nt76-1.png

*select return View inside AlbumList.js*

step2: import react-native library -> use scroll view

.. code::

          //path> src/components/AlbumList.js
          import React, { Component } from 'react';
          import { Text, ScrollView } from 'react-native';
          import axios from 'axios';
          import AlbumDetail from './AlbumDetail';

          //create class here
          class AlbumList extends Component {
            state = { albums: [] }; //set empty state

          componentWillMount() {
              console.log('componentWillMount in AlbumList');
              axios.get('https://rallycoding.herokuapp.com/api/music_albums')
              .then(response => this.setState({ albums: response.data }));
              //setState will help rerendering this page when new data come
            }

          renderAlbums() {
              return this.state.albums.map(album => <AlbumDetail key={album.title} album={album} />);
          }

          renderAlbums2() {
              console.log('calling renderAlbums2');
              return this.state.albums.map(album => <AlbumDetail key={album.title} album={album} />);
          }

          render() {
              console.log(this.state);
              return (
                <ScrollView>
                  { this.renderAlbums() }
                </ScrollView>
              );
            }
          }

          export default AlbumList;

*now we get the scrollable app*

.. image:: ../img/gs-native/nt76-2.png

.. image:: ../img/gs-native/nt76-3.png

7.7 handling user input with buttons

add button in cardsection of ‘AlbumList.js’

.. code::

            //path> src/components/AlbumDetail.js
            import React from 'react';
            import { Text, View, Image } from 'react-native';
            import Card from './Card'
            import CardSection from './CardSection'
            import Button from './Button'

            //create functional component here
            const AlbumDetail = ({ album }) => {
              const { title, artist, thumbnail_image, image } = album;
              const { thumbnailStyle, headerContentStyle,
            thumbnailContainerStyle,
                headerTextStyle, imageStyle } = styles;
            return (
                <Card>
                  <CardSection>
                  <View style={thumbnailContainerStyle}>
                    <Image
                      style={thumbnailStyle}

                    />
                  </View>
                  <View style={headerContentStyle}>
                    <Text style={headerTextStyle}>{title}</Text>
                    <Text>{artist}</Text>
                  </View>
                  </CardSection>

            <CardSection>
                  <Image
                    style={imageStyle}

                  />
                </CardSection>

                <CardSection>
                  <Button />
                </CardSection>
              </Card>
             );
            };

            const styles = {
              headerContentStyle: {
                flexDirection: 'column',
                justifyContent: 'space-around'
              },
              headerTextStyle: {
                fontSize: 18
              },
              thumbnailStyle: {
                height: 50,
                width: 50
              },
              imageStyle: {
                height: 300,
                flex: 1,
                width: null
              },
              thumbnailContainerStyle: {
                justifyContent: 'center',
                alignItems: 'center',
                marginLeft: 10,
                marginRight: 10
              }
            };

            export default AlbumDetail;

add button.js under ‘src/components’

..code ::

            //src/components/button.js
            import React from 'react';
            import { Text, TouchableOpacity } from 'react-native';

            const Button = () => {
              return (
                <TouchableOpacity>
                  <Text>Click me!!!</Text>
                </TouchableOpacity>
              );
            };

            export default Button;

7.8 styling of buttons with UX considerations

..code ::

            //src/components/button.js
            import React from 'react';
            import { Text, TouchableOpacity } from 'react-native';

            const Button = () => {
              const { buttonStyle, texStyle } = styles;
            return (
                <TouchableOpacity style={buttonStyle}>
                  <Text style={texStyle}>
                    Click me!!!
                  </Text>
                </TouchableOpacity>
              );
            };

            const styles = {
              texStyle: {
                alignSelf: 'center',
                color: '#007aff',
                fontSize: 16,
                fontWeight: '600',
                paddingTop: 10,
                paddingBottom: 10
              },
              buttonStyle: {
                flex: 1,
                alignSelf: 'stretch',
                backgroundColor: '#fff',
                borderRadius: 5,
                borderWidth: 1,
                borderColor: '#007aff',
                marginLeft: 5,
                marginRight: 5
              }
            }

            export default Button;

.. image:: ../img/gs-native/nt78-1.png

7.9 responding to user input

..code ::

            //path> src/components/AlbumDetail.js
            import React from 'react';
            import { Text, View, Image } from 'react-native';
            import Card from './Card'
            import CardSection from './CardSection'
            import Button from './Button'

            //create functional component here
            const AlbumDetail = ({ album }) => {
              const { title, artist, thumbnail_image, image } = album;
              const { thumbnailStyle, headerContentStyle, thumbnailContainerStyle,
                headerTextStyle, imageStyle } = styles;
            return (
                <Card>
                  <CardSection>
                  <View style={thumbnailContainerStyle}>
                    <Image
                      style={thumbnailStyle}

                    />
                  </View>
                  <View style={headerContentStyle}>
                    <Text style={headerTextStyle}>{title}</Text>
                    <Text>{artist}</Text>
                  </View>
                  </CardSection>
            <CardSection>
                    <Image
                      style={imageStyle}

                    />
                  </CardSection>
            <CardSection>
                    <Button onPress={() => console.log({ title })} />
                  </CardSection>
                </Card>
              );
            };
            const styles = {
              headerContentStyle: {
                flexDirection: 'column',
                justifyContent: 'space-around'
              },
              headerTextStyle: {
                fontSize: 18
              },
              thumbnailStyle: {
                height: 50,
                width: 50
              },
              imageStyle: {
                height: 300,
                flex: 1,
                width: null
              },
              thumbnailContainerStyle: {
                justifyContent: 'center',
                alignItems: 'center',
                marginLeft: 10,
                marginRight: 10
              }
            };

            export default AlbumDetail;

make change to Button.js

..code ::

            //path> src/components/Button.js
            import React from 'react';
            import { Text, TouchableOpacity } from 'react-native';

            const Button = ({ onPress }) => {
              const { buttonStyle, texStyle } = styles;
            return (
                <TouchableOpacity
                  onPress={onPress}
                  style={buttonStyle}
                >
                  <Text style={texStyle}>
                    Click me!!!
                  </Text>
                </TouchableOpacity>
              );
            };
            const styles = {
              texStyle: {
                alignSelf: 'center',
                color: '#007aff',
                fontSize: 16,
                fontWeight: '600',
                paddingTop: 10,
                paddingBottom: 10
              },
              buttonStyle: {
                flex: 1,
                alignSelf: 'stretch',
                backgroundColor: '#fff',
                borderRadius: 5,
                borderWidth: 1,
                borderColor: '#007aff',
                marginLeft: 5,
                marginRight: 5
              }
            }

            export default Button;

whenever you click a button, there will be a log in the console

.. image:: ../img/gs-native/nt79-1.png

7.10 linking between mobile apps : we want to take user to open mobile browser when they click the link

.. image:: ../img/gs-native/nt710-1.png

edit ‘AlbumDetail.js’ and add Linking button to open url

..code ::

            //path> src/components/AlbumDetail.js
            import React from 'react';
            import { Text, View, Image, Linking } from 'react-native';
            import Card from './Card'
            import CardSection from './CardSection'
            import Button from './Button'

            //create functional component here
            const AlbumDetail = ({ album }) => {
              const { title, artist, thumbnail_image, image, url } = album;
              const { thumbnailStyle, headerContentStyle, thumbnailContainerStyle,
                headerTextStyle, imageStyle } = styles;
            return (
                <Card>
                  <CardSection>
                  <View style={thumbnailContainerStyle}>
                    <Image
                      style={thumbnailStyle}

                    />
                  </View>
                  <View style={headerContentStyle}>
                    <Text style={headerTextStyle}>{title}</Text>
                    <Text>{artist}</Text>
                  </View>
                  </CardSection>
            <CardSection>
                    <Image
                      style={imageStyle}

                    />
                  </CardSection>
            <CardSection>
                    <Button onPress={() => Linking.openURL(url)} />
                  </CardSection>
                </Card>
              );
            };
            const styles = {
              headerContentStyle: {
                flexDirection: 'column',
                justifyContent: 'space-around'
              },
              headerTextStyle: {
                fontSize: 18
              },
              thumbnailStyle: {
                height: 50,
                width: 50
              },
              imageStyle: {
                height: 300,
                flex: 1,
                width: null
              },
              thumbnailContainerStyle: {
                justifyContent: 'center',
                alignItems: 'center',
                marginLeft: 10,
                marginRight: 10
              }
            };

            export default AlbumDetail;

.. image:: ../img/gs-native/nt710-2.png

7.11 setting button text by props

..code ::

            //path> src/components/AlbumDetail.js
            import React from 'react';
            import { Text, View, Image, Linking } from 'react-native';
            import Card from './Card'
            import CardSection from './CardSection'
            import Button from './Button'

            //create functional component here
            const AlbumDetail = ({ album }) => {
              const { title, artist, thumbnail_image, image, url } = album;
              const { thumbnailStyle, headerContentStyle, thumbnailContainerStyle,
                headerTextStyle, imageStyle } = styles;
            return (
                <Card>
                  <CardSection>
                  <View style={thumbnailContainerStyle}>
                    <Image
                      style={thumbnailStyle}

                    />
                  </View>
                  <View style={headerContentStyle}>
                    <Text style={headerTextStyle}>{title}</Text>
                    <Text>{artist}</Text>
                  </View>
                  </CardSection>
            <CardSection>
                    <Image
                      style={imageStyle}

                    />
                  </CardSection>
            <CardSection>
                    <Button onPress={() => Linking.openURL(url)}>
                      Buy Now
                    </Button>
                  </CardSection>
                </Card>
              );
            };
            const styles = {
              headerContentStyle: {
                flexDirection: 'column',
                justifyContent: 'space-around'
              },
              headerTextStyle: {
                fontSize: 18
              },
              thumbnailStyle: {
                height: 50,
                width: 50
              },
              imageStyle: {
                height: 300,
                flex: 1,
                width: null
              },
              thumbnailContainerStyle: {
                justifyContent: 'center',
                alignItems: 'center',
                marginLeft: 10,
                marginRight: 10
              }
            };

            export default AlbumDetail;

then you need to make ‘Button.js’ truely reuseable

..code ::

            import React from 'react';
            import { Text, TouchableOpacity } from 'react-native';
            const Button = ({ onPress, children }) => {
              const { buttonStyle, texStyle } = styles;
            return (
                <TouchableOpacity
                  onPress={onPress}
                  style={buttonStyle}
                >
                  <Text style={texStyle}>
                    {children}
                  </Text>
                </TouchableOpacity>
              );
            };
            const styles = {
              texStyle: {
                alignSelf: 'center',
                color: '#007aff',
                fontSize: 16,
                fontWeight: '600',
                paddingTop: 10,
                paddingBottom: 10
              },
              buttonStyle: {
                flex: 1,
                alignSelf: 'stretch',
                backgroundColor: '#fff',
                borderRadius: 5,
                borderWidth: 1,
                borderColor: '#007aff',
                marginLeft: 5,
                marginRight: 5
              }
            }
            export default Button;

.. image:: ../img/gs-native/nt711-1.png

7.12 app wrap-up

- state only available to Class object, only update it with ‘this.setState()’

------------

Step8: Authentication with Firebase
-----------------------------------

.. image:: ../img/gs-native/nt8-1.png

.. image:: ../img/gs-native/nt8-2.png

.. image:: ../img/gs-native/nt8-3.png

8.1 start new application by typing

..code ::
            $ react-native init auth
            $ react-native run-ios

8.2 then open Atom to edit code (we want ios and Android to use the same code) -> create ‘app.js’ inside ‘src’ folder

.. image:: ../img/gs-native/nt82-1.png

8.3 copying reusable components -> components from previous section put inside ‘src/components/common’

.. image:: ../img/gs-native/nt83-1.png

.. image:: ../img/gs-native/nt83-2.png

.. image:: ../img/gs-native/nt83-3.png

.. image:: ../img/gs-native/nt83-4.png

8.4 what is Firebase?

.. image:: ../img/gs-native/nt84-1.png

.. image:: ../img/gs-native/nt84-2.png

.. image:: ../img/gs-native/nt84-3.png

then you will see the following screen

.. image:: ../img/gs-native/nt84-4.png

choose ‘email/password’ for the signup method

.. image:: ../img/gs-native/nt84-5.png

.. image:: ../img/gs-native/nt84-6.png

8.5 Firebase client setup

- install Firebase through npm

..code ::

            $ npm install --save firebase

on Firebase click ‘web setup’

.. image:: ../img/gs-native/nt85-1.png

edit ‘app.js’ to add life-cycle method to get user logged in before proceeding to the rendered page

..code ::

            //app.js
            import React, { Component } from 'react';
            import { View, Text } from 'react-native';
            import firebase from 'firebase';
            import { Header } from './components/common';

            class App extends Component {
              // need to add Life-Cycle method
              componentWillMount() {
                firebase.initializeApp({
                  apiKey: "AIzaSyB7elfzAI02vPbasgtvN3BdQ4jAjBL3IQw",
                  authDomain: "auth-1f3eb.firebaseapp.com",
                  databaseURL: "https://auth-1f3eb.firebaseio.com",
                  projectId: "auth-1f3eb",
                  storageBucket: "auth-1f3eb.appspot.com",
                  messagingSenderId: "201442596072"
                });
              }

            render() {
                return (
                  <View>
                    <Header headerText="Authentication" />
                    <Text>An App!</Text>
                  </View>
                );
              }
            }

            export default App;

8.6 Login form scaffolding

.. image:: ../img/gs-native/nt86-1.png

create a login form

..code ::

            //LoginForm.js
            import React, { Component } from 'react';
            import { View } from 'react-native';
            import { Button, Card, CardSection } from './common';

            class LoginForm extends Component {
              render() {
                return (
                  <Card>
                    <CardSection />
                    <CardSection />

                    <CardSection>
                      <Button>
                        Login
                      </Button>
                    </CardSection>

            </Card>
                );
              }
            }

            export default LoginForm;

in ‘app.js’ add LoginForm

..code ::

            //app.js
            import React, { Component } from 'react';
            import { View } from 'react-native';
            import firebase from 'firebase';
            import { Header } from './components/common';
            import LoginForm from './components/LoginForm'

            class App extends Component {
              // need to add Life-Cycle method
              componentWillMount() {
                firebase.initializeApp({
                  apiKey: 'AIzaSyB7elfzAI02vPbasgtvN3BdQ4jAjBL3IQw',
                  authDomain: 'auth-1f3eb.firebaseapp.com',
                  databaseURL: 'https://auth-1f3eb.firebaseio.com',
                  projectId: 'auth-1f3eb',
                  storageBucket: 'auth-1f3eb.appspot.com',
                  messagingSenderId: '201442596072'
                });
              }

            render() {
                return (
                  <View>
                    <Header headerText="Authentication" />
                    <LoginForm />
                  </View>
                );
              }
            }

            export default App;

after successfully run, you will see

.. image:: ../img/gs-native/nt86-2.png

8.7 Handling user inputs

edit ‘LoginForm.js’

..code ::

            import React, { Component } from 'react';
            import { View, TextInput } from 'react-native';
            import { Button, Card, CardSection } from './common';

            class LoginForm extends Component {
              render() {
                return (
                  <Card>
                    <CardSection>

                    </CardSection>
                    <CardSection />

            <CardSection>
                      <Button>
                        Login
                      </Button>
                    </CardSection>

            </Card>
                );
              }
            }

            export default LoginForm;

you will see

.. image:: ../img/gs-native/nt87-1.png

8.8 More on handling user inputs

8.9 How to create controlled components

8.10 Making text inputs from scratch

8.11 A focus on passing props

8.12 Making the input pretty

8.13 Wrapping up the inputs

8.14 Password inputs

------------

Step9: Processing Authentication Credentials
--------------------------------------------

------------

Step10: Digging Deeper with Redux
---------------------------------

------------

Step11: Back to React
----------------------

------------

Step12: Rendering List the Right Way
------------------------------------

------------

Step13: Not Done Yet
--------------------

------------

Step14: Handling Data in React vs Redux
---------------------------------------

------------

Step15: Don’t Mutate that State
-------------------------------

------------

Step16: Navigating Users Around
-------------------------------

------------

Step17: Firebase as a Data Store
--------------------------------

------------

Step18: Code Reuse — Edit vs Create
-----------------------------------

------------

Step19: Bonus
-------------

- Animated charts in React Native https://medium.com/the-react-native-log/animated-charts-in-react-native-using-d3-and-art-21cd9ccf6c58
- https://github.com/mdvacca/rn-d3-art-charts
- https://medium.com/the-react-native-log/animated-charts-in-react-native-using-d3-and-art-21cd9ccf6c58

------------

Step20: Make ARKit App
----------------------

- https://medium.com/@HippoAR/how-to-make-your-own-arkit-app-in-5-minutes-using-react-native-9d7ce109a4c2
- https://github.com/HippoAR/react-native-arkit
- https://www.npmjs.com/package/react-native-arkit

------------

TROUBLESHOOT
------------

1. After installing ESLint if you get ‘run-ios’ not recognized, you need to reinstall react-native and update to the latest version

..code ::

            step1: remove 'node_modules' folder from the project
            step2:
            $ npm install
            $ npm install --save react-native@latest
            $ npm install --save react@latest

2. Interesting development tools

.. note ::  1. JS playground with real-time feedbacks

            https://stephengrider.github.io/JSPlaygrounds/

3. Interesting framework

3.1 Meteor and React for Realtime Apps

.. image:: ../img/gs-native/tbs31-1.png
