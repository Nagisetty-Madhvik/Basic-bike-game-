package main

import (
	"fmt"
	"math/rand"
	"strings"
	"time"
)

const (
	trackLength = 20
)

type Bike struct {
	position int
}

func (b *Bike) move() {
	b.position++
}

func main() {
	
	rand.Seed(time.Now().UnixNano())

	
	bike1 := Bike{}
	bike2 := Bike{}

	
	fmt.Println("Track:")
	for i := 0; i < trackLength; i++ {
		fmt.Print("-")
	}
	fmt.Println()
	fmt.Printf("Bike 1: %s\n", strings.Repeat(" ", bike1.position)+"X")
	fmt.Printf("Bike 2: %s\n", strings.Repeat(" ", bike2.position)+"X")

	
	for {
		
		bike1.move()
		bike2.move()

		
		fmt.Println("Track:")
		for i := 0; i < trackLength; i++ {
			fmt.Print("-")
		}
		fmt.Println()
		fmt.Printf("Bike 1: %s\n", strings.Repeat(" ", bike1.position)+"X")
		fmt.Printf("Bike 2: %s\n", strings.Repeat(" ", bike2.position)+"X")

		
		if bike1.position >= trackLength {
			fmt.Println("Bike 1 wins!")
			break
		} else if bike2.position >= trackLength {
			fmt.Println("Bike 2 wins!")
			break
		}

		
		time.Sleep(time.Second / 2)
	}
}
