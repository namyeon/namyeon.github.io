import Slider from 'react-animated-slider';
import 'react-animated-slider/build/horizontal.css';

<Slider>
  {content.map((article, index) => <div key={index}>
    <h2>{article.title}</h2>
    <div>{article.description}</div>
  </div>)}
</Slider>
