'use client'

import { useState } from 'react'
import { Button } from "@/components/ui/button"
import { Input } from "@/components/ui/input"
import { Label } from "@/components/ui/label"
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from "@/components/ui/select"
import { Textarea } from "@/components/ui/textarea"

export default function Component() {
  const [practiceType, setPracticeType] = useState('')
  const [otherPracticeType, setOtherPracticeType] = useState('')

  const handleSubmit = (event: React.FormEvent<HTMLFormElement>) => {
    event.preventDefault()
    // Here you would typically send the form data to your backend
    console.log('Form submitted')
  }

  return (
    <div className="max-w-md mx-auto p-6 bg-white rounded-lg shadow">
      <h1 className="text-2xl font-bold mb-6">Healthcare Provider Information</h1>
      <form onSubmit={handleSubmit} className="space-y-4">
        <div>
          <Label htmlFor="fullName">Full Name</Label>
          <Input id="fullName" required />
        </div>
        <div>
          <Label htmlFor="phoneNumber">Phone Number</Label>
          <Input id="phoneNumber" type="tel" required />
        </div>
        <div>
          <Label htmlFor="email">Email Address</Label>
          <Input id="email" type="email" required />
        </div>
        <div>
          <Label htmlFor="practiceNumber">Practice Number</Label>
          <Input id="practiceNumber" required />
        </div>
        <div>
          <Label htmlFor="practiceName">Practice Name</Label>
          <Input id="practiceName" required />
        </div>
        <div>
          <Label htmlFor="practiceType">Practice Type</Label>
          <Select onValueChange={setPracticeType} required>
            <SelectTrigger>
              <SelectValue placeholder="Select practice type" />
            </SelectTrigger>
            <SelectContent>
              <SelectItem value="general">General Practice</SelectItem>
              <SelectItem value="specialist">Specialist</SelectItem>
              <SelectItem value="dental">Dental</SelectItem>
              <SelectItem value="other">Other</SelectItem>
            </SelectContent>
          </Select>
        </div>
        {practiceType === 'other' && (
          <div>
            <Label htmlFor="otherPracticeType">Specify Other Practice Type</Label>
            <Input
              id="otherPracticeType"
              value={otherPracticeType}
              onChange={(e) => setOtherPracticeType(e.target.value)}
              required
            />
          </div>
        )}
        <Button type="submit" className="w-full">Submit</Button>
      </form>
    </div>
  )
}
