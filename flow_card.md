import React from 'react';

import {

  setsessionData,

  checkPropVal,

  shallowRender,

  findByDataTestAttribute,

} from '../../../../../utils/unitTestUtil';

import FlowCard from '../components/FlowCard/FlowCard';



const getFlowCardProps = () => {

  return {

​    dataIndex: 2,

​    length: 2,

​    cardConfig: [

​      {

​        gridWidth: '100',

​        mobileGridWidth: '100',

​        name: 'txnId',

​        noBorderBottom: true,

​        pbottom: false,

​        ptop: false,

​        render: React.createElement('div', null, 'Test'),

​        type: 'TitleGrid',

​        stickyId: null,

​      },

​      {

​        gridWidth: '100',

​        mobileGridWidth: '100',

​        name: 'description',

​        noBorderBottom: false,

​        pbottom: false,

​        ptop: false,

​        render: React.createElement('div', null, 'Test'),

​        stickyId: 'test',

​      },

​    ],

​    styleConfig: {

​      alternatingBg: false,

​      cardBorder: false,

​      cardPadding: true,

​    },

  };

};



describe('Contributions Dashboard Components', () => {

  beforeEach(() => {

​    setsessionData();

  });



  afterEach(() => {

​    sessionStorage.clear();

  });



  describe('FlowCard component', () => {

​    let component;

​    let props;

​    beforeEach(() => {

​      props = getFlowCardProps();

​      component = shallowRender(FlowCard, false, props);

​    });



​    it('Should render FlowCard', () => {

​      expect(component).toMatchSnapshot();

​    });



​    it('Should check proptypes', () => {

​      checkPropVal(FlowCard, props, false);

​    });



​    it('Should not render display none', () => {

​      props = { ...props, length: 3 };

​      component = shallowRender(FlowCard, false, props);

​      expect(component).toMatchSnapshot();

​    });



​    it('Should render empty card', () => {

​      props = { ...props, cardConfig: null };

​      component = shallowRender(FlowCard, false, props);

​      const noDataEle = findByDataTestAttribute(component, 'no-data');

​      expect(noDataEle.text()).toBe('no data');

​    });



​    it('Should change grid width', () => {

​      props = {

​        ...props,

​        cardConfig: [

​          ...props.cardConfig,

​          {

​            gridWidth: '100',

​            mobileGridWidth: '190',

​            name: 'description',

​            noBorderBottom: false,

​            pbottom: false,

​            ptop: false,

​            render: React.createElement('div', null, 'Test'),

​            stickyId: 'test',

​          },

​        ],

​      };

​      component = shallowRender(FlowCard, false, props);

​      expect(component).toMatchSnapshot();

​    });



​    it('Should change grid width', () => {

​      props = {

​        ...props,

​        cardConfig: [

​          ...props.cardConfig,

​          {

​            gridWidth: '100',

​            mobileGridWidth: '100',

​            name: 'description',

​            noBorderBottom: false,

​            pbottom: false,

​            ptop: false,

​            render: React.createElement('div', null, 'Test'),

​            stickyId: 'test',

​          },

​        ],

​      };

​      component = shallowRender(FlowCard, false, props);

​      expect(component).toMatchSnapshot();

​    });

  });

});