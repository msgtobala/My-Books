**import** {

  setsessionData,

  checkPropVal,

  shallowRender,

  findByDataTestAttribute,

} **from** '../../../utils/unitTestUtil';

**import** Carousel **from** '../Components/Carousel/CarouselComponent';

**import** carouselArray **from** '../Components/Carousel/data';

**import** { colorMapping } **from** '../Components/InvestmentChart/config';



describe('Financial Advisor Component', () => {

  beforeEach(() => {

​    setsessionData();

  });



  afterEach(() => {

​    sessionStorage.clear();

​    jest.clearAllMocks();

  });



  describe('Carousel Component,', () => {

​    **let** props;

​    **let** carouselComponent;

​    **let** carouselInstance;



​    **const** getCarouselProps = () => {

​      **return** {

​        carouselData: [

​          { title: 'title', link: 'link', text: 'text', header: 'headre' },

​        ],

​        isLoadingCarousel: **true**,

​        requestData: jest.fn(),

​      };

​    };



​    beforeEach(() => {

​      props = getCarouselProps();

​      carouselComponent = shallowRender(Carousel, **true**, props);

​      carouselInstance = carouselComponent.instance();

​    });



​    it('should render <Carousel> component with given props', () => {

​      expect(carouselComponent).toMatchSnapshot();

​    });



​    it('Should Satisfy PropTypes', () => {

​      checkPropVal(Carousel, props, **true**);

​    });



​    it('Should pass componentWillMount', () => {

​      carouselInstance.componentDidMount();

​      expect(props.requestData).toBeCalled();

​    });



​    it('Should execute learn more function', () => {

​      jest.spyOn(window, 'open').mockImplementation(() => {});

​      **let** updatedProps = { ...props, isLoadingCarousel: **false** };

​      carouselComponent = shallowRender(Carousel, **true**, updatedProps);

​      **const** el = findByDataTestAttribute(carouselComponent, 'learn-more').at(0);

​      el.simulate('click');

​      expect(window.open).toHaveBeenCalled();

​    });



​    it('Should execute learn more function with empty link', () => {

​      jest.spyOn(window, 'open').mockImplementation(() => {});

​      **let** updatedProps = {

​        ...props,

​        isLoadingCarousel: **false**,

​      };

​      updatedProps.carouselData[0].link = **null**;

​      carouselComponent = shallowRender(Carousel, **true**, updatedProps);

​      **const** el = findByDataTestAttribute(carouselComponent, 'learn-more').at(0);

​      el.simulate('click');

​    });



​    it('Should load carousel data', () => {

​      **let** updatedProps = { ...props, isLoadingCarousel: **false** };

​      carouselComponent = shallowRender(Carousel, **true**, updatedProps);

​      **const** carouselComponents = findByDataTestAttribute(

​        carouselComponent,

​        'carousel-card'

​      );

​      expect(carouselComponents.length).toBe(1);

​    });



​    it('Should execute next and previous functions', () => {

​      **const** nextFn = jest.spyOn(carouselInstance, 'next');

​      **const** prevFn = jest.spyOn(carouselInstance, 'previous');

​      carouselInstance.carousel = {

​        ...carouselInstance.carousel,

​        next: jest.fn(),

​        prev: jest.fn(),

​      };

​      nextFn();

​      prevFn();

​      expect(nextFn).toHaveBeenCalledTimes(1);

​      expect(prevFn).toHaveBeenCalledTimes(1);

​    });

  });



  describe('Data check for carousel', () => {

​    it('Should return data', () => {

​      expect(carouselArray.length).toBe(3);

​    });

  });



  describe('Initialize chart Config', () => {

​    **let** data = [

​      {

​        name: 'Total Equity Select',

​      },

​      {

​        name: 'Growth Select',

​      },

​    ];



​    it('Should return color mapping', () => {

​      **const** result = colorMapping(data);

​      expect(result.length).toBe(data.length);

​    });



​    it('Should not return color mapping', () => {

​      **const** result = colorMapping([]);

​      expect(result).toBeUndefined();

​    });



​    it('Should not return color mapping', () => {

​      data = [{ name: 'this-name-not-exists' }];

​      **const** result = colorMapping(data);

​      expect(result.length).toBe(1);

​    });

  });

});