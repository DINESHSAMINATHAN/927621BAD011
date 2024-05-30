DEVELOPE AVERAGE CALCULATOR HTTP MICROSERVICE

1.Set up a React project using Create React App.
2.Create a component for the Average Calculator microservice.
3.Implement the logic to fetch numbers from the provided test server and handle responses.
4.Maintain state for storing numbers, calculating the average, and managing the window size.
5.Render the response data in the desired format.

import React, { useState } from 'react';

const AverageCalculator = () => {
  const [windowPrevState, setWindowPrevState] = useState([]);
  const [windowCurrState, setWindowCurrState] = useState([]);
  const [numbers, setNumbers] = useState([]);
  const [avg, setAvg] = useState(0);

  const fetchNumbers = async (numberType) => {
    try {
      const response = await fetch(http://localhost:9876/numbers/${numberType});
      const data = await response.json();
      setWindowPrevState(data.windowPrevState);
      setWindowCurrState(data.windowCurrState);
      setNumbers(data.numbers);
      setAvg(data.avg);
    } catch (error) {
      console.error('Error fetching numbers:', error);
    }
  };

  return (
    <div>
      <button onClick={() => fetchNumbers('p')}>Fetch Prime Numbers</button>
      <button onClick={() => fetchNumbers('f')}>Fetch Fibonacci Numbers</button>
      <button onClick={() => fetchNumbers('e')}>Fetch Even Numbers</button>
      <button onClick={() => fetchNumbers('r')}>Fetch Random Numbers</button>

      <div>
        <h2>Window Previous State: {windowPrevState.join(', ')}</h2>
        <h2>Window Current State: {windowCurrState.join(', ')}</h2>
        <h2>Numbers: {numbers.join(', ')}</h2>
        <h2>Average: {avg}</h2>
      </div>
    </div>
  );
};

This is a basic example to get you started. You'll need to further enhance it based on your specific requirements, including error handling, styling, and potentially more complex state management.

