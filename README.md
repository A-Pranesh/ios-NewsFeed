# ios-NewsFeed
import React , {Component} from 'react';
import {StyleSheet, Text, View,ListView} from 'react-native';
import data from './data.json';
import Post from './Post';

const dataSource = new ListView.DataSource({
	rowHasChanged: (r1, r2) => r1!==r2,
});

export default class News extends React.Component{
	state = {
		dataSource: dataSource.cloneWithRows(data.posts),
	};
	render() {
		return (
				<View style = {styles.Container} >
					<View style = {styles.Toolbar} >
						<Text style = {styles.Title}> NewsFeed </Text>
					</View>
					<ListView
						dataSource = {this.state.dataSource}
						renderRow = {post => <Post {...post} />}
						style = {styles.Lists}
						contentContainerStyle = {styles.post}
					/>
				</View>
			);
	}
}

const styles = StyleSheet.create({
	Container: {
		flex: 1,
	},
	Toolbar: {
		backgroundColor: 'grey',
		padding: 10,
		paddingTop: 20,
	},
	Title: {
		color: 'red',
		fontSize: 20,
		fontWeight: 'bold',
		textAlign: 'center',
	},
	Lists: {
		backgroundColor: 'white',
		paddingTop: 5,
		paddingBottom: 5,
	},
	post: {
		flexDirection: 'row',
		flexWrap: 'wrap',
		justifyContent: 'center',
	},
})
