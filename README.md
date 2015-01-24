# vote_sim
class Game
	def initialize 
		main_menu
	end
end
 
 
class Human
	attr_accessor :name
	def initialize(name)
		@name = name
	end
end
 
class Politician < Human
	attr_accessor :party
	@@politicians = []
	def initialize(name, party)
		super name
		@party = party
 
		@@politicians << self
	end
	def self.all
		@@politicians
	end
	def to_s
		"#{name}, of the #{party} party."
	end
end
 
class Person < Human
	attr_accessor :party
	@@people = []
	def initialize(name, party)
		super name
		@party = party
 
		@@people << self
	end
	def self.all
		@@people
	end
end
 
 
def list
	puts "politicians or voters"
	list_choice = gets.chomp
	case list_choice
	when "politicians"
		p Politician.all
	when "voters"
		p Person.all
	end
end
 
def update
	puts "Do you want to update a politician or a voter?"
	case gets.chomp
	when "politician"
		puts "who do you want to update?"
			name = gets.chomp
		puts "whats the new name"
		new_name = gets.chomp
		puts "what is #{new_name}'s party"
		new_party = gets.chomp
		Politician.all.each { |bro| 
			if name == bro.name?
				bro.name = new_name
				bro.party = new_party
			end }
	when "voter"
		puts "who do you want to update?"
			name = gets.chomp
		puts "whats the new name"
		new_name = gets.chomp
		puts "what is #{new_name}'s party"
		new_party = gets.chomp
		Person.all.each { |bro| 
			if name == bro.name 
				bro.name = new_name
				bro.party = new_party
			end }
		main_menu
	end
end
 
		
 
 
 
def create_individual
	puts "politician or person"
	case gets.chomp
	when "politician"
		puts "Name?"
		name = gets.chomp
		puts "what party does #{name} belong to?"
		party = gets.chomp
		Politician.new(name, party)
	when "person"
		puts "Name?"
		name = gets.chomp
		puts "what party does #{name} associate with?"
		party = gets.chomp
		Person.new(name, party)
	end
end
 
def main_menu
	puts "What would you like to do? Create, List, Update, Vote"
	case gets.chomp
	when "create"
		create_individual
		main_menu
	when "list"
		list
		main_menu
	when "sample"
		Politician.new("Jeff", "Republican")
		Person.new("Charles", "Socialist")
		main_menu
	when "update"
		update
		main_menu
	end
end
start = Game.new
