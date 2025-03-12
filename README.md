# Guess-the-number-with-React
I have developed the "Guess the Number" game, where the player had unlimited chances to guess a random number between 1 and 20. If the guess was incorrect, they were told whether it was higher or lower until they guessed correctly. I created two components: App, which handled logic, and Result, which displayed messages. 
npx create-react-app guess
cd guess
"dependencies": {
    "@testing-library/jest-dom": "^5.16.5",
    "@testing-library/react": "^13.4.0",
    "@testing-library/user-event": "^13.5.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-scripts": "5.0.1",
    "web-vitals": "^2.1.4"
}
// App.js

import React, { Component } from 'react'
import Result from './components/Result'
import './App.css'
class App extends Component {

	static defaultProps = {
		secret: Math.floor(Math.random() * 20) + 1
	}

	constructor(props) {
		super(props)
		this.state = { term: '' }

		this.handleChange = this.handleChange.bind(this)
	}

	handleChange(event) {
		this.setState({
			[event.target.name]: event.target.value
		})
	}

	render() {
		return (
			<div className='container'>
				<div className='head'>
					<label htmlFor='term'>
						Guess Number between 1 to 20
					</label>
				</div>
				<input
					id='term'
					type='text'
					name='term'
					value={this.state.term}
					onChange={this.handleChange}
				/>

				<Result term={this.state.term}
					secretNum={this.props.secret} />
			</div>
		)
	}
}
export default App
