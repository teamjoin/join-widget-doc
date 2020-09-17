# join-components  

[![NPM](https://img.shields.io/npm/v/join-web-components.svg)](https://www.npmjs.com/package/join-web-components)

### Classic integration
`<script type="text/javascript" src="https://unpkg.com/join-web-components@2.X.X"></script>`

And then you can directly use our web components in your html files

`<join-list-container team-id="join-demo" alias="join-stories-default-all" ></join-list-container>`

or

`<join-iframe team-id="join-demo" alias="join-stories-default-all" height="700"></join-iframe>`

### React integration example
Install the package
- `yarn add join-web-components` or `npm install join-web-components`

Find out the [codesandbox.io](https://codesandbox.io/s/join-web-components-react-nhrds)

## join-list-component  
| Attribute             |  Type         | Default       |  Description |  
| :-------------------- | :---------------------------------------------------- | :---------------------------- | :---------------------------------------------------------------------------------------------------------------- |  
| team-id               | string                                                |                               | Id of the team to match the associated stories from the Studio                                                    |  
| alias                 | string                                                |                               | Alias of the container to match the associated stories from the Studio                                            |  
| shape                 | enum: { 'round', 'square', 'rounded-square', 'card' } | 'round'                       | Different shape of container item ([see demo](https://demo.teamjoin.fr/ "see demo"))                              |  
| justify-content       | enum: { 'flex-start', 'center', 'flex-end' }          | 'center'                      | Flex alignement applied on the container                                                                          |  
| limit                 | number                                                | 10                            | Number of stories fetched                                                                                         |  
| sort-by               | enum: { 'asc', 'desc', 'ordered' }                    | 'desc'                        | Either you can sort by last edition date (asc or desc) either by an order fixed from the Studio                   |
| border-colors         | array                                                 | [ 'red', 'orange', 'yellow' ] | Array of colors (Hexa, rgba...) used to define the color gradient of the outer border (minimum 2 colors)          |  
| height                | number                                                | 100                           | Unit use to calculate the size of the bubble size (bubbles height and width are proportional to this value but not equal) |  
| spacing               | number                                                |                               | The space in px between a bubble and the edge of the container. Distance between 2 bubbles will be twice this value. |  
| show-labels           | boolean                                               | false                         | Option to display the labels under the story (You need to configure the label in the studio)                      |  
| labels-style          | object                                                | {}                            | Add css properties to add to your label. ([see demo](https://codesandbox.io/s/join-web-components-uqf3j)) Warning : padding need to be configure through verticalPadding and horizontalPadding. Properties should be write in CamelCase. |  
| labels-line-count     | number                                                | 1                             | Number of lines the label can be written on |  
| inner-color           | string                                                | 'white'                       | The color of the inner border |  
| outer-border-size     | number                                                | 2                             | Size of the outer border |  
| inner-border-size     | number                                                | 2                             | size of the inner border |  
  
### Integration Examples

#### Containers With Default Labels

```html
<join-list-container  team-id="join-demo"
                      alias="join-stories-default-all"
                      show-labels
></join-list-container>
```

#### Containers With customized Label

```html
<join-list-container 
                    team-id="join-demo"
                    alias="join-stories-default-all"
                    spacing="25"
                    show-labels
                    labels-style='{
                        "fontSize" : 11.2,
                        "fontWeight":550,
                        "backgroundColor": "white",
                        "fontFamily": "museo-sans, sans-serif",
                        "verticalPadding":3, "horizontalPadding":10,
                        "textTransform": "uppercase",
                        "textDecoration": "none"
                    }'
                    sort-by="ordered"
    ></join-list-container>
```

## join-iframe  

| Attribute             |  Type         | Default       |  Description |  
| :-------------------- | :---------------------------------------------------- | :---------------------------- | :---------------------------------------------------------------------------------------------------------------- |  
| team-id               | string                                                |                               | id of the team to match the associated stories from the Studio                                                    |  
| alias                 | string                                                |                               | Alias of the container to match the associated stories from the Studio                                            |  
| story-info            | string                                                |                               | The URL of the story to display if there is no team-id and alias                                                  |  
| mobile-break-point    | number                                                | 1024                          | Screen width where the iframe switch between mobile and desktop mode                                              |  
| border-colors         | array                                                 | [ 'red', 'orange', 'yellow' ] | Array of colors (Hexa, rgba...) used to define the color gradient of the outer border (minimum 2 colors)          |  
| height                | number                                                | 100                           | Unit use to calculate the size of the card size (card height and width is proportional to this value but not equal)                                                                     |  
| inner-color           | string                                                | 'white'                       | The color of the inner border |  
| outer-border-size     | number                                                | 2                             | Size of the outer border |  
| inner-border-size     | number                                                | 0                             | size of the inner border |  
| disable-history       | boolean                                               | false                         | Option to disable the history manipulation from the widget. Must be activated if you are have troubling behaviour when closing the story in mobile |  


### Examples

#### Iframe with default parameters
```html
<div style="display: flex;width: 100%; justify-content: center;">
      <join-iframe height="500" team-id="join-demo" alias="join-stories-default-all"></join-iframe>
</div>
```

#### Iframe with url
```html
<join-iframe height="500" story-info="https://demo.join-stories.com/naturalizer-UkSVfXhMT/"></join-iframe>
```