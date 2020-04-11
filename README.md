# react-tabs-dynamic-render


```
import React, { Component } from "react";
import { TabContent, TabPane, Nav, NavItem, NavLink, Card, CardTitle, CardText, Row, Col } from 'reactstrap';
import classnames from 'classnames';

class Tabs extends Component {
  constructor(props) {
    super(props);
    this.state = {
      activeTab: 1,
      arrayNew: 
      [
        1, 2, 3, 4, 5, 6, 7, 8, 9
      ]
    };
  }

  toggle = tab => {
    console.log(tab, "tab");
    let { activeTab } = this.state;
    if (activeTab !== tab) {
      this.setState({
        activeTab: tab
      })
    };
  }


  render() {
    let { activeTab } = this.state;

    return (
      <div>
        <Breadcrumb link="ImportantDates" parent="Admin" />
        <div className="container-fluid">
          <div className="edit-profile">
            <div className="row ">
              <div className="col-xl-12">
                <Alert />
                <div>
                  <div >
                    <Nav tabs>
                      {this.state.arrayNew.map(item => {
                        return (
                          <NavItem>
                            <NavLink
                              className={classnames({ active: activeTab === `'${item}'` })}
                              onClick={() => { this.toggle(`'${item}'`) }}
                            >
                              Tab{item}
                            </NavLink>
                          </NavItem>
                        )
                      })}
                    </Nav>
                    {this.state.arrayNew.map(item => {
                      return (

                        <TabContent activeTab={activeTab}>
                          <TabPane tabId={`'${item}'`}>
                            <Row>
                              <Col sm="12">
                                <h4>Tab {`${item}`} Contents</h4>
                              </Col>
                            </Row>
                          </TabPane>
                        </TabContent>
                      )
                    })}
                  </div>

                </div>
              </div>
            </div>
          </div>
        </div>


      </div>
    );
  }
}

export default connect Tabs;
```
